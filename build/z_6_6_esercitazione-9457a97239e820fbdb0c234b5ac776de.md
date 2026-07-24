# Esercitazione 6.6: Algoritmo iterativo OS-EM

## Dati

- Fantoccio cerebrale 2D `111 x 111` pixel, file `brain.npy`.
- Funzione `Calcolo_A.py` già utilizzata nelle esercitazioni precedenti.
- Scheletro dell'esercitazione, file `Scheletro_Es7.py`.
- Scheletro della funzione `Calcolo_Hblock.py`, con descrizione della struttura e del funzionamento richiesti.

## Svolgere

### Punto 1: blocchi della matrice di sistema

Creare una funzione esterna, partendo da `Calcolo_Hblock.py`, per estrarre i blocchi della matrice di sistema con cui ricostruire i singoli subset del sinogramma. La funzione deve restituire `nblock` segmenti della matrice di sistema `A` e, per ciascun blocco, deve tenere traccia delle proiezioni che fanno parte del subset associato.

### Punto 2: OS-EM

Implementare l'algoritmo OS-EM per la ricostruzione del sinogramma rumoroso generato ai punti precedenti, eseguendo la correzione degli artefatti durante la ricostruzione.

### Punto 3: relazione tra subset e iterazioni

Visualizzare il risultato della ricostruzione OS-EM usando diverse combinazioni per il numero di subset, cioè il fattore di accelerazione, e per il numero di iterazioni di ricostruzione.

### Punto 4: accelerazione OS-EM

Misurare i tempi di esecuzione di una ricostruzione ML-EM e di ricostruzioni OS-EM, considerando il tempo totale e non le singole sub-iterazioni. Verificare la velocizzazione del processo di ricostruzione dovuta all'uso dei subset.

## Codice di partenza

```python
# -*- coding: utf-8 -*-
"""
Esercitazione  


"""


import numpy as np
import matplotlib.pyplot as plt
import scipy  # Per caricare il file .mat
# from numpy.random import poisson
from Calcolo_A import Calcolo_A
from Calcolo_Hblock import Calcolo_Hblock
import time


# Carica il sinogramma rumoroso e  gli artefatti generati nell'esercitazione precedente 
# Alternativa: genera di nuovo il sinogramma, copiando il codice della scorsa esercitazione
# ... 

# %% Parametri
imgsize       = phantom.shape
N             = imgsize[0]
pixels        = np.prod(imgsize)

N_projections = 157 #180
N_positions   = 180 #157
sinosize      = (N_positions, N_projections)

bins          = np.prod(sinosize)
iter_mlem     = 50
iter_osem     = 2
nblock        = 25


    
# %%
# RICOSTRUZIONE OSEM - CALCOLO DEI BLOCCHI DELLA MATRICE DI SISTEMA
# Creare una funzione esterna (partire dal file Calcolo_Hblock.PY fornito)
# per l'estrazione dei blocchi della matrice di sistema con cui ricostruire
#i singoli subset del sinogramma.
#
# La descrizione della funzione è fornita nel file dedicato, è importante
# assicurarsi che restituisca in output 'nblock' segmenti della matrice di
# sistema A e, per ciascuno di essi, tenga traccia delle proiezioni che 
# fanno parte del subset a cui è associato un determinato blocco.

# %%
# RICOSTRUZIONE OSEM
# Implementare l'algoritmo OS-EM per la ricostruzione del sinogramma
# rumoroso generato nell'esercitazione precedente. 

print('Ricostruzione immagine con OSEM ..')

OSEM = np.zeros((N, N, iter_osem * nblock))
activity = np.ones((pixels, 1))

Hblock = Calcolo_Hblock(A, N_positions,N_projections, nblock)

for iter in range(iter_osem):
    print(f'\nOSEM step: {iter + 1} \n')

    # loop over subsets
    for iset in range(nblock):
        print(f'iset: {iset + 1} \n')
        # ...
      


#%%   ANALISI DELLA RELAZIONE TRA NUMERO DI SUBSET E NUMERO DI ITERAZIONI OSEM:
# % Visualizzare il risultato della ricostruzione OSEM usando diverse combinazioni
# % di valori per il numero di subset (fattore di accelerazione) e il numero di 
# % iterazioni di ricostruzione.

# %% VALUTAZIONE DELL'ACCELARAZIONE OTTENUTA CON ALGORITMO OS-EM
# % Misurare i tempi di esecuzione di una ricostruzione ML-EM (totale, non
# % delle singole iterazioni) e di una ricostruzione OS-EM e verificare che
# % ci sia una velocizzazione del processo di ricostruzione a parità di
# % iterazioni utilizzate

# % NOTA BENE:
# % - mettersi nella condizione iter_mlem = iter_osem*nblock
# % - verificare tutte e 3 le combinazioni possibili 
# %   (es. iter_mlem=50; iter_osem=2 nblock=25; iter_osem=25 nblock=2)
# % - assicurarsi di misurare l'effettivo tempo di ricostruzione, privo di
# %   sovraccarichi legati a salvataggio di ricostruzioni intermedie e
# %   visualizzazione degli stessi
```


### `Scheletro_Calcolo_Hblock.py`

```python
# -*- coding: utf-8 -*-


import numpy as np

def Calcolo_Hblock(H, nproj, npos, nblock):
    """
    Trasformazione della Matrice di Sistema in una matrice a blocchi.

    Args:
        H (numpy.ndarray): Matrice di sistema (sinogramma_righe * sinogramma_colonne x numero_pixel_immagine).
        nproj (int): Numero di proiezioni angolari (colonne del sinogramma).
        npos (int): Numero di locazioni del rilevatore (righe del sinogramma).
        nblock (int): Numero di subset in cui suddividere H.

    Returns:
        list: Una lista di dizionari, dove ogni dizionario rappresenta un blocco e contiene:
              - 'block' (numpy.ndarray): Matrice Hk relativa all'i-esimo blocco di proiezioni.
              - 'projections' (numpy.ndarray): Vettore delle proiezioni (indici degli angoli)
                                                appartenenti all'i-esimo blocco.
    """

    Hblock = []

    # ordina i subset in modo casuale
    starts = np.random.permutation(nblock)
    
    # alternativa: ordina in modo da massimizzare la differenza tra subset
    # successivi 
    
   
    for iset in range(nblock):  # In Python gli indici partono da 0
        print(f'\nEstrazione sottomatrice per il subset: {iset + 1} \n')
        istart = starts[iset]
        # ...
       
    return Hblock

if __name__ == '__main__':
    # Esempio di utilizzo (da adattare ai tuoi dati reali)
    nproj = 20
    npos = 10
    nblock = 4
    num_pixels = 5  # Esempio per il numero di colonne di H
    H = np.random.rand(npos * nproj, num_pixels)

    H_blocks = Calcolo_Hblock(H, nproj, npos, nblock)

    for i, block_data in enumerate(H_blocks):
        print(f"\nBlocco {i + 1}:")
        print("  Proiezioni (indici):", block_data['projections'])
        print("  Dimensione della matrice Hk:", block_data['block'].shape)
```


## Soluzione

![Risultati dal PDF originale 1](./images/santarelli/z_6_6_p02.png)

![Risultati dal PDF originale 2](./images/santarelli/z_6_6_p03.png)


