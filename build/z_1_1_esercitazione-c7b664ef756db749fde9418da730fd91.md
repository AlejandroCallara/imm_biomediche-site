# Esercitazione 1.1: Emissione spontanea ed emissione stimolata

## Dati

- `h`: costante di Planck, `4.14e-15 eV*s` (`6.63e-34 J*s`)
- `k`: costante di Boltzmann, `8.6173e-5 eV*K^-1` (`1.3806e-23 J*K^-1`)
- `c`: velocità della luce, `2.998e8 m/s`
- conversione da gradi Celsius a Kelvin: `K = °C + 273.15`

## Eseguire

1. Valutare il rapporto tra emissione spontanea ed emissione stimolata nella banda delle onde elettromagnetiche con lunghezza d'onda `300e-9 <= lambda <= 0.5 m`, cioè tra onde radio e ultravioletto, per una temperatura `T = 20 °C`.
2. Mostrare il grafico risultante con assi logaritmici, rilevando per quale valore di `lambda0` e quindi della frequenza `nu0` le due emissioni si equivalgono, cioè `log(EmissSpont/EmissStim) = 0`.
3. Valutare come varia il valore di `lambda0` e/o `nu0` al variare della temperatura, per `15 °C <= T <= 40 °C`.

## Librerie Python

```python
import numpy as np
import matplotlib.pyplot as plt
```

## Codice di partenza

```python

import numpy as np
import matplotlib.pyplot as plt

K = 8.6173e-5
h = 4.14e-15
T = 20 + 273.15  # K = (°C + 273.15)
c = 2.28e8
Lambda = np.arange(0.5, 300e-9, -1e-7)  # Genera array da 0.5 a 300e-9 con passo -1e-7
ni = c / Lambda
points = len(ni)
#.implementazione della formula:
A_Bro = .....
LA_Bro = .... # A_Bro in logaritmo base e 


plt.figure(figsize=(5, 5))
# aggiungere qui i comandi per fare il grafico 
# N.B. le lunghezze d'onda hanno valore dal più grande al più piccolo


# Punto 2: - valutare come varia il valore di   e/o 0 al variare della temperatura, per 15°C <= T <=40°C
Temp = np.arange(15, 41, 2) + 273.15
cont = 0
L = []  # Inizializza L come una lista vuota
for temp_val in Temp:
    
    ....
    ....
    

Temp = Temp - 273.15
L = np.array(L)  # converte lista in array numpy.
plt.figure(figsize=(5, 5))
plt.plot(Temp, L)
# grafico dei risultati

plt.show()
```

## Soluzione 

![Grafici risultanti dal PDF originale 1](./images/santarelli/z_1_1_p02.png)


