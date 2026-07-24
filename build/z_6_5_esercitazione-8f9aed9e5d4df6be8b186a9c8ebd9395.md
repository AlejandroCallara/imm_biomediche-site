# Esercitazione 6.5: Algoritmo iterativo EM-ML

## Dati

- Fantoccio cerebrale 2D `111 x 111` pixel, file `brain.npy`.
- Funzione Python `Calcolo_A.py` già utilizzata nell'esercitazione precedente.
- Scheletro dell'esercitazione, file `Scheletro_Es6.py`.

## Svolgere

### Ricostruzione ML-EM

1. Implementare l'algoritmo ML-EM per la ricostruzione dell'immagine dal sinogramma rumoroso presente nel file scheletro.
2. Valutare la qualità della ricostruzione a seconda che vengano corretti o meno i disturbi simulati.

## Codice di partenza

```python
# -*- coding: utf-8 -*-
"""
Scheletro Esercitazione N. 6

"""


import numpy as np
import matplotlib.pyplot as plt

from Calcolo_A import Calcolo_A


# Carica il file .npy
loaded_data = np.load('brain.npy',allow_pickle=True)
data_dict = loaded_data.item()

# 3. Distingui le matrici e stampane le forme (o altri attributi)
print("Contenuto del file 'brain.npy':")
print(f"Chiavi disponibili: {data_dict.keys()}")
brain = data_dict['BRAIN']

phantom = brain.astype(np.float64)
imgsize = phantom.shape
N = imgsize[0]
pixels = np.prod(imgsize)

N_projections = 157 #180
N_positions = 180 #157
sinosize = (N_positions, N_projections)


bins = np.prod(sinosize)
iter_mlem = 50


plt.figure(1)
plt.imshow(phantom)
plt.axis('off')
plt.title('Phantom')


# Simulazione scansione
print('Creazione del sinogramma simulato ...')
A = Calcolo_A(N_positions,N_projections,  imgsize[0],imgsize[1]) # Richiama la funzione definita sopra

# forward projection
X0 = phantom.reshape(pixels, 1)
ideal_sinogram = np.dot(A,X0) 

tmp = ideal_sinogram.reshape(sinosize)
plt.figure(figsize=(10, 5))
plt.imshow(tmp.T), plt.title('ideal sinogram')
plt.show()

# Generazione artefatti
print('Simulazione artefatti e aggiunta rumore ...')
RF = 0.02  # random factor
SF = 0.05  # scatter factor
AF = 0.03  # attenuation factor

# ATTENUAZIONE
u = np.zeros(imgsize)
u[brain > 0] = AF  # Usa la comparazione diretta con l'array
att = np.dot(A, u.reshape(pixels, 1))
attenuation = np.exp(-att)  
# tmp = attenuation.reshape(sinosize)
# plt.figure(figsize=(10, 5))
# plt.imshow(tmp.T), plt.title('attenuation')
# plt.show()

# EFFETTI ADDITIVI DI BACKGROUND (RANDOM COUNTS)
M = np.mean(attenuation * ideal_sinogram)  
random_noise = M * RF * np.random.randn(*sinosize)
random_noise = random_noise.reshape(bins,1)- np.min(random_noise) # solo valori positivi
# tmp = random_noise.reshape(sinosize)
# plt.figure(figsize=(10, 5))
# plt.imshow(tmp.T), plt.title('random_noise')
# plt.show()

# EFFETTI ADDITIVI DI BACKGROUND (SCATTERING)
xgauss = np.linspace(-1, 1, N_positions)
scatter = (np.exp(-(xgauss**2) / (2 * 0.0208)))  
scatter = (scatter - np.min(scatter)) / (np.max(scatter) - np.min(scatter))
tmp1 = scatter * SF * M
tmp = np.tile(tmp1, (N_projections,1)) # ripeti per 180 volte
tmp = tmp.T
scatter = tmp.reshape(bins, 1)
background_effects = scatter + random_noise  
# tmp = background_effects.reshape(sinosize)
# plt.figure(figsize=(10, 5))
# plt.imshow(tmp), plt.title('background_effects')
# plt.show()

# AGGIUNGERE LE COMPONENTI DI DISTURBO AL SINOGRAMMA
sinogram = attenuation * ideal_sinogram + random_noise + scatter  
sinogram = np.random.poisson(sinogram)  
tmp = sinogram.reshape(sinosize)
plt.figure(figsize=(10, 5))
plt.imshow(tmp.T), plt.title('completely noisy sinogram')
plt.show()



# %%
# RICOSTRUZIONE MLEM
# Implementare l'algoritmo ML-EM per la ricostruzione del sinogramma
# rumoroso generato ai punti precedenti. Valutare la qualità della
# ricostruzione a seconda che vengano corretti o meno i disturbi simulati.
# Salvare l'immagine intermedia ricostruita ad ogni iterazione in un
# vettore 3D (N,N,iter_mlem) 

print('Ricostruzione immagine con MLEM ..')
# Inizializzazione del vettore Likelihood
L = np.zeros((iter_mlem, 1))
# Per salvare le ricostruzioni intermedie
MLEM = np.zeros((imgsize[0],imgsize[1], iter_mlem))
# stima iniziale uniforme dell'immagine
activity = np.ones((pixels, 1))

# MAPPA DI SENSITIVITA'
# (cfr. primo termine a denominatore della formula ML-EM ed OS-EM)
sensitivity = np.dot(A.T, np.ones((bins, 1)))

for iter in range(iter_mlem):
    print(f'MLEM step: {iter + 1} ')
    # ...
```


### `Calcolo_A.py`

```python
# -*- coding: utf-8 -*-


import numpy as np
from scipy.sparse import coo_matrix

def Calcolo_A(na, nb, nx, ny):
    """
    Calcola la matrice di sistema A per la tomografia.

    Args:
        na: Numero di proiezioni.
        nb: Numero di misure (numero di righe del sinogramma).
        nx: Numero di righe dell'immagine finale.
        ny: Numero di colonne dell'immagine finale.

    Returns:
        Matrice di sistema A (scipy.sparse.coo_matrix).
    """

    x = np.arange(nx) - (nx ) / 2  # Coordinate centrate sull'immagine
    y = -1 * (np.arange(ny) - (ny) / 2)  # Asse y invertito
    x, y = np.meshgrid(x, y)  # Griglia di coordinate
    mask = np.ones((nx, ny), dtype=bool)  # Maschera di 1 logici
    x = x[mask]
    y = y[mask]
    np_ = len(x)  # Numero di punti
    angle = np.arange(1, na + 1) / na * np.pi - np.pi / 2
    s = np.cos(angle[:, np.newaxis]) * x[np.newaxis, :] + np.sin(angle[:, np.newaxis]) * y[np.newaxis, :]
    s = s + (nb + 1) / 2   # Scala s per indici positivi
    ibl = np.floor(s).astype(int)  # Indici interi positivi 
 
    val = 1 - (s - ibl)  # Valore peso per il bin
    ii = ibl + np.arange(na)[:, np.newaxis] * nb * np.ones((1,np_), dtype=int) 
    
    good = (ibl >= 0) & (ibl < nb)  # Indici validi
    if not np.all(good):
        print('Warning: FOV too small')
    nc = nx * ny  # Numero di pixel dell'immagine
    jj = np.where(mask.flatten())[0]  # Indici dei pixel
    jj = np.tile(jj, (na, 1))
    val1 = 1 - val
    A1 = coo_matrix((val[good], (ii[good], jj[good])), shape=(nb * na, nc))  # Bin sinistro
    A2 = coo_matrix((val1[good], (ii[good], jj[good])), shape=(nb * na, nc))  # Bin destro
    
    A = A1 + A2
    A = np.flipud(A.toarray()) # flipud viene applicato ad un array numpy. quindi prima converto la matrice sparsa in array.
    return A
```


## Soluzione


![Risultati dal PDF originale 1](./images/image_z_6_5.png)

![Risultati dal PDF originale 2](./images/santarelli/z_6_5_p02.png)

![Risultati dal PDF originale 3](./images/santarelli/z_6_5_p03.png)


