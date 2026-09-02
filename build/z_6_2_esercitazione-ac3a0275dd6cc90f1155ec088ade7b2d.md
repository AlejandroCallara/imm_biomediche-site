# Esercitazione 6.2: Algoritmo iterativo ART

## Dati

- Sinogrammi dei fantocci Shepp-Logan a 32 punti e del fantoccio circolare con rumore, per `0° <= theta < 180°`, con `Delta theta = 1°`, calcolati nelle esercitazioni precedenti.
- Funzione `A = Calcolo_A(na, nb, nx, ny)` per la generazione della matrice di sistema.

## Svolgere

Ricostruire le immagini da sinogrammi mediante l'algoritmo ART, con il numero di iterazioni pari almeno al numero di proiezioni. Visualizzare le immagini risultanti.

## Codice di partenza

```python
# -*- coding: utf-8 -*-
"""
 Scheletro Esercitazione N. 5 del 08/10/2025
"""
import numpy as np
from skimage.transform import radon
import matplotlib.pyplot as plt
import time


from phantom import phantom
from Calcolo_A import Calcolo_A

# Immagini fantoccio
P_piccolo = ... #  phantom
teta1 = ...

# calcolo sinogramma per teta tra 0 e 179
Sin = radon(....)
nx, ny = # dimensioni immagine finale
nb, na = # dimensioni sinogramma



A = Calcolo_A(na, nb, nx, ny)
# Risoluzione problema inverso con metodo iterativo
f0 = np.zeros((nx, ny))  #inizializzazione immagine
f = f0.flatten()         # trasformata in vettore


nc = nx * ny
Ak = np.zeros((nb, nc))  # inizializzazione matrice di sistema
G = np.zeros((nb, 1))    # inizializzazione dell'errore (differenza tra la proiezione misurata e la proiezione stimata)

# ciclo per tutte le proiezioni
start_time = time.time()  # se si vuole stimare il tempo necessario ad eseguire l'algoritmo

for i in range(na):
    # definizione della sotto-matrice di sistema per il calcolo della proiezione:
    Ak = A[.....] # riga di A per ogni iterazione
    G = .... # errore 
    fk = .....  # proiezione al passo k-esimo
    f = f + fk  # aggiornamento dell'immagine
    
end_time = time.time()  # se si vuole stimare il tempo necessario ad eseguire l'algoritmo
# print(f"Tempo di esecuzione: {end_time - start_time} secondi")

RecART = ... # tornare dalla rappresentazione vettoriale dell'immagine a quella matriciale 

# Mostrare risultato
plt.figure(figsize=(10, 5))
...
plt.show()
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

![Risultati dal PDF originale 1](./images/image_z_6_4.png)

![Risultati dal PDF originale 2](./images/santarelli/z_6_4_p02.png)


