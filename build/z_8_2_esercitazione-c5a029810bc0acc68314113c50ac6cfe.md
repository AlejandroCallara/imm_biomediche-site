# Esercitazione 8.2: Mappe metaboliche da immagini dinamiche [18F]FDG-PET brain

## Dati

Nella cartella `DATI brain PET FDG` sono presenti:

- `Dataset.npy`, data dictionary con i campi:
  - `Volume`: matrice 4D, cioè 3D più tempo, con immagini dinamiche cerebrali [18F]FDG;
  - `PETInfo`: struttura con informazioni sui dati, incluso il vettore dei tempi.
- `ROI_mask_slice7_frame4.npy`: maschera di una ROI che copre un vaso, usata per generare la input function `AIF`.
- `ROI_mask_slice20_frame22.npy`: maschera di una ROI del tessuto, materia grigia.
- `ROI_mask_slice20_frame23.npy`: maschera di una ROI che include tutto il cervello nell'immagine.
- `Scheletro Es 10a_Patlak.py`.
- `Scheletro Es 10b_AnalyticMethod.py`.

## Punto 0: costruzione delle TAC da ROI

### 0.a Input Function

Data la ROI predefinita in `ROI_mask_slice7_frame4.npy` e le immagini, costruire la curva `AIF`. Ogni punto della `AIF` è il valor medio dei pixel nella ROI a un tempo `ti`.

### 0.b TAC tissutale

Data la ROI predefinita in `ROI_mask_slice20_frame22.npy` e le immagini, costruire la curva tempo-attività tissutale.

### 0.c Asse dei tempi

Importare dalla struttura `PETInfo` nel file `Dataset.npy` il vettore dei tempi:

```python
time_TAC = PETInfo['time']
time_TAC = time_TAC[0][0].flatten()
```

I valori sono in secondi.

## Punto 1.A: metodo grafico su ROI

Calcolare il fractional uptake nella ROI selezionata:

1. visualizzare i dati dei punti 0.a e 0.b in un grafico di Patlak;
2. nei punti più lineari, per esempio i punti 18-24, eseguire una regressione lineare e calcolare il coefficiente angolare `m`;
3. valutare la velocità di utilizzo, fractional uptake, del glucosio `Ri`.

Parametri:

- `LCbrain = 0.81`
- `Cp = 100 mg/dl`
- `Ri = m * (Cp / LC)` in `[mg/g*min]`
- densità `rho_brain = 1.15 g/cm^3`

## Punto 1.B: metodo grafico voxel-wise

Su ciascun pixel incluso nella ROI selezionata, valutare il fractional uptake con la stessa modalità usata per la ROI del punto 1.A. La curva `AIF` è quella valutata al punto 0. Costruire la mappa del metabolismo.

## Punto 2.A: metodo analitico su ROI

1. Implementare la funzione `Ct`, cioè `def modello_exp(k, time)`, nel file `Scheletro Es 10b_AnalyticMethod.py`.
2. Implementare le formule del modello usando la funzione `Ct = modello_conv_IF(k, time, Cp)` già fornita.
3. Usare `modello_conv_IF` come ingresso dell'algoritmo di ottimizzazione `curve_fit`.

Opzioni di ottimizzazione:

```python
lb = np.array([0.0, 0.0, 0.0, 0.0, 0.0])    # K1 k2 k3 k4 vB
ub = np.array([10.0, 1.0, 1.0, .05, 1.0])   # K1 k2 k3 k4 vB
k0 = np.array([0.1, 0.1, 0.1, 0.001, 0.1])  # K1 k2 k3 k4 vB
```

## Punto 2.B: metodo analitico voxel-wise

Data la ROI che copre tutto il cervello, `ROI_mask_slice20_frame23.npy`, generare curve `TAC` per ogni pixel incluso nella ROI:

1. eseguire il fitting voxel per voxel con il modello, come nel punto 2.A;
2. costruire una mappa per ogni parametro del modello;
3. costruire la mappa del macro-parametro `Ri = K1*k3/(k2+k3)*Cp/LC`.

## Codice di partenza

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Scheletro Es 10a. Patlak

"""

import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import trapezoid
import time


def patlak_func(TAC, Cp, time, LC, glicemia):
    """Calcola il Patlak influx constant"""
    
    R = ....

    return R



# %% ------ Codice  PARTE 0 (caricamento files e costruzione curve   ----

print("1. Inizio caricamento dati...")

# Carica il file .npy
loaded_data = np.load('Dataset.npy',allow_pickle=True)
data_dict = loaded_data.item()

# 3. Distingui i vettori e stampane le forme (o altri attributi)
print("Contenuto del file 'Dataset.npy':")
print(f"Chiavi disponibili: {data_dict.keys()}")

PETInfo = data_dict['PETinfo']
Volume = data_dict['Volume']    

#  -----------  Caricamento ROIs ----
images_to_process = [
    {'idx_slice': 7, 'idx_frame': 4},
    {'idx_slice': 20, 'idx_frame': 23},
    {'idx_slice': 20, 'idx_frame': 22},
]
ROI = None
ROI1 = None
ROI2 = None
plt.figure(figsize=(12, 10))
for ind, img_info in enumerate(images_to_process):
    idx_slice = img_info['idx_slice']
    idx_frame = img_info['idx_frame']
    file_path = f'ROI_mask_slice{idx_slice}_frame{idx_frame}.npy'
    loaded_data = np.load(file_path, allow_pickle=True)
    print(f"Tipo di dato caricato: {type(loaded_data)}")
    # Puoi ora accedere agli elementi del dizionario caricato
    if ind == 0:   
        ROI = loaded_data        
        plt.subplot(2, 2, 1)      
        plt.imshow(Volume[:, :, idx_slice, idx_frame], cmap='gray')
        plt.imshow(ROI, cmap='jet', alpha=0.3)
        plt.title('ROI Selezionata per Input Function')
        plt.axis('off')
 
    elif ind == 1:
        ROI1 = loaded_data
        plt.subplot(2, 2, 2)
        plt.imshow(Volume[:, :, idx_slice, idx_frame], cmap='gray')
        plt.imshow(ROI1, cmap='jet', alpha=0.3)
        plt.title('ROI Selezionata per Ct')
        plt.axis('off')

    elif ind == 2:
        ROI2 = loaded_data
        plt.subplot(2, 2, 3)
        plt.imshow(Volume[:, :, idx_slice, idx_frame], cmap='gray')
        plt.imshow(ROI2, cmap='jet', alpha=0.3)
        plt.title('ROI Brain')
        plt.axis('off')

plt.show(block=False) 

# --- Inizio del programma principale ---  
glicemia = 1.0  # mg/cc
glicemia = glicemia / 1.15  # mg/g
time_TAC = PETInfo['time']
time_TAC = time_TAC[0][0].flatten()



# %% Costruire le curve TAC della Input function Cp e del tessuto
....

IF = ....
....
TAC =....

# costruzione asse dei tempi:
time_TAC = ....


plt.figure()
plt.plot(time_TAC, IF, 'k', linewidth=2)
plt.plot(time_TAC, TAC, linewidth=2)
plt.legend(['AIF', 'TAC from ROI'])
plt.xlabel('time(sec)')
plt.show(block=False) 



# %% ------ Codice  PARTE 1 Dalle curve TAC, costruire il Patlak-plot ( pre-definire una 
# funzione e richiamarla qui), e graficarne il risultato

.....

# %% Calcolare il fractional Uptake R:
    
R =...    



# %% ------ Codice  PARTE 2  COSTRUZIONE della mappa:
# per ogni pixel incluso nella maschera ROI2, calcolare il valore R mediante Patlak

...
R[i,j] =

# Mostrare la mappa di fractional uptake Rij risultante  e valutare il tempo 
#  necessario per costruire la mappa : 


end_time = time.time()
print(f"Tempo di esecuzione: {end_time - start_time} secondi")

plt.figure()
plt.imshow(Map)
plt.axis('off')
plt.colorbar()
plt.title('Fractional Uptake Map R from Patlak graphs')
```


### `Scheletro Es 10b_AnalyticMethod.py`

```python
# -*- coding: utf-8 -*-
"""
Scheletro Es 10.b


"""




import matplotlib.pyplot as plt
import numpy as np
from scipy.optimize import curve_fit
from scipy.interpolate import interp1d
from scipy.signal import convolve
from scipy.io import savemat
import time as time_module




# %% Funzione da implementare:
def modello_exp(k, time):
  """
DA IMPLEMENTARE ( funzione analoga al LSQfit_example, vista a lezione):
  Args:
    k (list or numpy.ndarray): Un array o lista di 4 elementi contenenti i valori di k.
    time (float or numpy.ndarray): Il valore o array di valori del tempo.

  Returns:
    numpy.ndarray: Il valore o array di valori di Ct calcolato.
    
    
% Questa funzione deve prendere in ingresso le 4 costanti del modello 
% compartimentale e il vettore dei tempi,  
% e svolge al suo interno la conversione nel set di variabili ausiliarie 
% per poi calcolare C_t(t) 

  """
  
....

  return Ct

# %% Funzioni già implementate:
    
def modello_conv_IF(k, time, Cp):
    """ La funzione applica il modello convolutivo per generare la curva Ct 
    da una generica Input Function"""
    vB = k[4]
    dt = 0.1
    t = np.arange(0, time[-1] + dt, dt)
    t = np.array(t)
    Cp = np.array(Cp)
    
    IF_func = interp1d(time.flatten(), Cp.flatten(), kind='linear', fill_value=0, bounds_error=False)
    IF = np.maximum(0, IF_func(t))

    sol = convolve(modello_exp(k, t), IF, mode='full') * dt
    tsol = np.arange(0, 2 * t[-1] + dt, dt)

    sol_func = interp1d(tsol, sol, kind='linear', fill_value=0, bounds_error=False)
    sol_interp = np.maximum(0, sol_func(time.flatten()))
 # % Taking into account blood fraction in tissue: (N.B.: we don't account natural radioactive
 #  decay: Our data are compensated yet!!!)

    Ct = (1 - vB) * sol_interp + vB * Cp
    Ct[Ct <= 0] = np.finfo(float).eps
    return Ct



def fun(t, k1, k2, k3, k4, vB):
    """ funzione da dare in input alla funzione che esegue il fitting non lineare 
    curve_fit (vedi sotto) """
    k = np.array([k1, k2, k3, k4, vB])
    return modello_conv_IF(k, t, mIF)


# %% inizio del codice principale:

# %% Riprendiamo le ROI e le curve TAC dall'esercitazione 10a.

print("1. Inizio caricamento dati...")
    
# Carica il file .npy
loaded_data = np.load('Dataset.npy',allow_pickle=True)
data_dict = loaded_data.item()

# 3. Distingui i vettori e stampane le forme (o altri attributi)
print("Contenuto del file 'Dataset.npy':")
print(f"Chiavi disponibili: {data_dict.keys()}")

PETInfo = data_dict['PETinfo']
Volume = data_dict['Volume']   

     
time_TAC = PETInfo['time']
time_TAC = time_TAC[0][0].flatten()    

#  -----------  Caricamento ROIs ----
images_to_process = [
    {'idx_slice': 7, 'idx_frame': 4},
    {'idx_slice': 20, 'idx_frame': 23},
    {'idx_slice': 20, 'idx_frame': 22},
]
ROI = None
ROI1 = None
ROI2 = None
plt.figure(figsize=(12, 10))
for ind, img_info in enumerate(images_to_process):
    idx_slice = img_info['idx_slice']
    idx_frame = img_info['idx_frame']
    file_path = f'ROI_mask_slice{idx_slice}_frame{idx_frame}.npy'
    loaded_data = np.load(file_path, allow_pickle=True)
    print(f"Tipo di dato caricato: {type(loaded_data)}")
    # Puoi ora accedere agli elementi del dizionario caricato
    if ind == 0:   
        ROI = loaded_data        
        plt.subplot(2, 2, 1)      
        plt.imshow(Volume[:, :, idx_slice, idx_frame], cmap='gray')
        plt.imshow(ROI, cmap='jet', alpha=0.3)
        plt.title('ROI Selezionata per Input Function')
        plt.axis('off')
 
    elif ind == 1:
        ROI1 = loaded_data
        plt.subplot(2, 2, 2)
        plt.imshow(Volume[:, :, idx_slice, idx_frame], cmap='gray')
        plt.imshow(ROI1, cmap='jet', alpha=0.3)
        plt.title('ROI Selezionata per Ct')
        plt.axis('off')

    elif ind == 2:
        ROI2 = loaded_data
        plt.subplot(2, 2, 3)
        plt.imshow(Volume[:, :, idx_slice, idx_frame], cmap='gray')
        plt.imshow(ROI2, cmap='jet', alpha=0.3)
        plt.title('ROI Brain')
        plt.axis('off')

plt.show(block=False) 



# Plot delle curve tempo-attività
plt.figure()
plt.plot(time_TAC, mIF, linewidth=2, label='IF')
plt.plot(time_TAC, mTAC, 'r', linewidth=2, label='Tissue')

# Ottimizzazione non lineare (lsqcurvefit)
lb = np.array([0.0, 0.0, 0.0, 0.0, 0.0])
ub = np.array([10.0, 1.0, 1.0, .05, 1.0])
k0 = np.array([0.1, 0.1, 0.1, 0.001, 0.1])



popt, pcov = curve_fit(.....)
TAC_fit = .... # curva risultante dal fitting, cioè con i parametri stimati nel fitting

# mostrare in un grafico: le curve di partenza (Cp e Ct, e il risultato del fitting:) 
plt.plot(....)
plt.title('Time-Activity Curves')
plt.xlabel('Time (s)')
plt.ylabel('Actvity')
plt.grid(True) 
plt.legend()
plt.show()

print(f"Estimated k: {k_est}")

#%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%-----------------

YN = input("vuoi continuare? N/Y 0/1: ")
if YN == '1' or YN.lower() == 'y' or YN=='1':
    
# ripetere il fitting implementato, per ogni pixel nella ROI3 
# N.B. il tempo di calcolo delle mappe parametriche è molto lungo. Si consiglia
# di eseguire il programma e salvarne i risultati, segnalando il tempo di calcolo    
    
....      
        
    end_time = time_module.time()
    print(f"Elapsed time: {end_time - start_time} seconds")

    SAVE_k = k_est_all.reshape(128, 128, 5)
# mostrare  le mappe dei parametri stimati: K1, k2, k3, k4, Vb, Ki
  
    plt.figure()
    plt.subplot(2, 3, 1)
    ....

    plt.subplot(2, 3, 2)
    ....

    plt.subplot(2, 3, 3)
    ...

    plt.subplot(2, 3, 4)
   ...
    plt.subplot(2, 3, 5)
    ...
    
    Ki = SAVE_k[:, :, 0] * SAVE_k[:, :, 2] / (SAVE_k[:, :, 1] + SAVE_k[:, :, 2] + np.finfo(float).eps)
    ....
    
    # %%% PER CONFRONTO CON PATLAK:
    #  mostrare la mappa del fractional uptake R derivato dai microparametri 
    #  K1, k2 e k3:    
    ....
    
    plt.imshow(np.flipud(Ri), origin='lower', vmin=0, vmax=0.03)
    plt.colorbar()
    plt.title('Fractional Uptake R:')
```

## Soluzione

I risultati sono riportati nelle diapositive del corso. 
