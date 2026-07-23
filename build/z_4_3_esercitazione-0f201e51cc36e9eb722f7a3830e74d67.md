# Esercitazione 4.3: Ricostruzione di Immagini RM

<!-- Origine: Esercitazione_2025_2026_4_CALLARA_SANTARELLI.docx -->

## k-spazio campionato in maniera non uniforme

Di seguito è riportato lo scheletro del file da produrre per completare l’esercitazione, mentre i file *spirale64giri.mat* e *spirale32giri.mat* contengono ciascuno
- FOVxy: dimensione, in cm, del campo di vista lungo x e y
- I: immagine ricostruita da campionamento uniforme
- f_nonh_x: coordinata x dei campioni della spirale (nel piano di Fourier)
- f_nonh_y: coordinata y dei campioni della spirale (nel piano di Fourier)
- mu: k-spazio campionato sulla spirale (con coordinate date da f_nonh_x e f_nonh_y)

```
import numpy as np
import matplotlib.pyplot as plt
from scipy.io import loadmat
from scipy.spatial import Voronoi, voronoi_plot_2d
from my_polygon_area import polygon_area

# 1. Load data

# 2. mostrare a video l'immagine originale

# 3. mostrare a video la spirale di campionamento

# 4. definire le coordinate spaziali (x,y), dal FOV e le dimensioni dell'immagine I

# 5. definire le aree utilizzando il diagramma di Voronoi 

# 6. mostrare a video il diagramma di Voronoi

# 7. calcolare il valore delle aree delle celle di Voronoi
# utilizzare la funzione fornita: my_polygon_area.py


# 8. Definire la matrice E della trasformata inversa discreta di Fourier, 
# il cui elemento (n,m) è dato da: E[n, m] = np.exp(2 * np.pi * 1j * (rx[n] * f[m, 0] + ry[n] * f[m, 1])). 
# rx[n] e ry[n] sono due vettori che contengono le coordinate [x,y] vettorizzate 
# (usare meshgrid e vettorizzare al fine di utilizzare un'unico indice
# per lo scorrimento del vettore) dell'immagine; 
# f è un vettore che contiene [f_nonh_x,f_nonh_y]

# 9. creare il vettore f che contiene f_nonh_x, f_nonh_y

# 10. creare la griglia spaziale e vettorizzare r

# 11. calcolare la matrice della trasformata inversa E

# 12. Pesare i dati e moltiplicarli per la matrice E riconstruendo l'immagine.
```

### B.1 
Eseguire la ricostruzione delle immagini, con i seguenti passi (implementazione della
trasformata diretta di Fourier):
- Importare la spirale a 64 giri;
- Definire le coordinate spaziali (x e y sulla base del FOV e della risoluzione);
- Definire le aree con cui pesare i dati, mediante la funzione Voronoi;
- Calcolare le aree di ciascuna cella di Voronoi mediante la funzione fornita dal docente my_polygon_area.py;
- trascurare i dati in periferia, con area non definibile (NaN);
- Definire la matrice di Fourier E; usarla sui dati (cioè i valori della matrice mu) pesati con le aree per
ricostruire l’immagine;
- Visualizzare l’immagine risultante

### B.2 
Ripetere i punti precedenti per la spirale a 32 giri (sotto-campionamento radiale)

### B.3 
Ripetere i punti precedenti per la spirale a 64 giri, campionando un punto sì ed uno no
(sotto-campionamento temporale)

SOLUZIONE B

<img src="./images/z_4_3/z_4_3_img_01.png" alt="Esercitazione 4.3" style="width:100%;">

<img src="./images/z_4_3/z_4_3_img_02.png" alt="Esercitazione 4.3" style="width:100%;">

<img src="./images/z_4_3/z_4_3_img_03.png" alt="Esercitazione 4.3" style="width:100%;">

<img src="./images/z_4_3/z_4_3_img_04.png" alt="Esercitazione 4.3" style="width:100%;">

*Soluzione spirale 64 giri*

<img src="./images/z_4_3/z_4_3_img_05.png" alt="Esercitazione 4.3" style="width:100%;">

<img src="./images/z_4_3/z_4_3_img_06.png" alt="Esercitazione 4.3" style="width:100%;">

<img src="./images/z_4_3/z_4_3_img_07.png" alt="Esercitazione 4.3" style="width:100%;">

*Soluzione spirale 32 giri*

<img src="./images/z_4_3/z_4_3_img_08.png" alt="Esercitazione 4.3" style="width:100%;">

<img src="./images/z_4_3/z_4_3_img_09.png" alt="Esercitazione 4.3" style="width:100%;">

<img src="./images/z_4_3/z_4_3_img_10.png" alt="Esercitazione 4.3" style="width:100%;">

*Soluzione spirale 64 giri + sottocampionamento*