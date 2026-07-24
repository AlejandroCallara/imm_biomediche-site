# Esercitazione 3.2: Traccianti per misure di metabolismo [18F]FDG-PET

## Dati

Dati PET cardiaci relativi a due pazienti, nella cartella "DATI cuore PET FDG".

Per il soggetto 1, file `DATI_SUBJ1.npy`:

- `time`: tempo in secondi;
- `LV`: curva tempo-attività dalla cavità del ventricolo sinistro, `Cp(t)`;
- `lat`: curva tempo-attività relativa a una regione della parete laterale, `mid lat`;
- `sept`: curva tempo-attività relativa a una regione del setto, `mid sept`.

Per il soggetto 2, file `DATI_SUBJ2.npy`:

- `time`: tempo in secondi;
- `LV`: curva tempo-attività dalla cavità del ventricolo sinistro, `Cp(t)`;
- `lat`: curva tempo-attività relativa a una regione della parete laterale, `mid lat`;
- `ant`: curva tempo-attività relativa a una regione della parete anteriore, `mid ant`.

## Svolgere

1. Visualizzare le curve tempo-attività di tutti i segmenti, per entrambi i casi.
2. Visualizzare i dati in un grafico di Patlak.
3. Per ciascuna curva calcolata dal grafico di Patlak, nei punti più lineari, cioè da un tempo `t*` in poi, eseguire un fitting lineare con `p = np.polyfit(x, y, n)` e `n = 1`, quindi calcolare il coefficiente angolare `m`.
4. Dai risultati precedenti, valutare la velocità di utilizzo, o fractional uptake, del glucosio `Ri` in ciascuna regione della parete cardiaca e per ciascun paziente.

## Parametri

- `LC = 0.67`
- `Cp = 100 mg/dl`, glicemia
- `R = m * (Cp / LC)` in `[mg/g*min]`
- densità `rho = 1.08 g/cm^3`, con `rho = Massa / Volume`

Si consiglia di implementare la costruzione del grafico di Patlak e il calcolo del fractional uptake `Ri` come funzione:

```python
def patlak_func(TAC, Cp, time, LC, glicemia):
    ...
```

La funzione servirà in una esercitazione successiva per costruire le mappe di fractional uptake.

## Codice di partenza

```python
# -*- coding: utf-8 -*-
"""
 Esercitazione 9 22/10/2025
"""

import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import trapezoid


#====================================================
#
#  CASO I
#
#=======================================================



# Carica il file .npy
loaded_data = np.load('DATI_SUBJ1.npy',allow_pickle=True)
data_dict = loaded_data.item()


# Plot delle curve di concentrazione
plt.figure(facecolor='white')
.....

# Geenrazione del Patlak plot: 
....

# Esecuzione del fit lineare
....

# Plot del Patlak graph e fitting:
plt.figure()
.....

# Calcolo del fractional uptake (R):
glicemia = 1 / 1.08  # 1 [mg/g] divido per la densità: ottengo glicemia in mg/g
LC = 0.67  # Lumped Constant adimensionale
Rlat = ...
Rsept = ....

print(f"R: parete lat = {Rlat:.4f} [mg/g*min]    setto= {Rsept:.4f} [mg/g*min]")

plt.show()

# %%---------------------------------------------------------------------
#====================================================
#
#  CASO II  :analogo al CASO I
#
#=======================================================

....
```


## Soluzione

![Risultati dal PDF originale 1](./images/santarelli/z_3_2_p02.png)

![Risultati dal PDF originale 2](./images/santarelli/z_3_2_p03.png)


