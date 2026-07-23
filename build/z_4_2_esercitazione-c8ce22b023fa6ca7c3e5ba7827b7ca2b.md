# Esercitazione 4.2: Ricostruzione di Immagini RM

<!-- Origine: Esercitazione_2025_2026_3_CALLARA_SANTARELLI.docx -->

## PARTE A: k-spazio uniformemente campionato

Il file *K_spazio_cuore.mat* contiene una matrice di dimensione $256 \times 256$ pixel e una matrice di dimensione $128 \times 128$ pixel di valori complessi (k-spazio) di una acquisizione della regione cardiaca. Le due matrici differiscono in termini di campionamento frequenziale.

### A.1 
Importare la matrice K_S e ricostruire l’immagine tramite la trasformata inversa di Fourier
bidimensionale. Visualizzarne il modulo.

### A.2
Selezionare la parte centrale del k-spazio del punto precedente, ovvero un quadrato di lato 40
pixel e ricostruire l’immagine (cioè: nuova matrice delle stesse dimensioni della precedente,
ma con i soli valori centrali uguali ai centrali del K_S_precedente e gli altri nulli). Visualizzare
l’immagine ricostruita.

### A.3 
Eliminare la parte centrale del k-spazio, ovvero un quadrato di lato 40 pixels e ricostruire
l’immagine (cioè: nuova matrice delle stesse dimensioni della precedente, ma con i soli valori
esterni al quadrato uguali agli esterni del K_S_precedente e gli altri nulli). Visualizzare
l’immagine ricostruita.

### A.4 
Sottocampionare il K-spazio, eliminando una riga sì ed una riga no (quindi: K-spazio con
numero di righe dimezzato) e ricostruire l’immagine. (sottocampionamento)
Valutazione del metodo per ridurre il n. di righe del k-spazio da acquisire:

### A.5 
Costruire un k-spazio dal 60% delle righe del k-spazio dato (cioè phase-FOV = .6) e ricostruire
l’immagine. Confrontare il risultato ottenuto con quello ottenuto nel punto A.1.

### A.6 
Costruire un k-spazio dal 60% delle righe del k-spazio dato; fare lo zero pending del K-spazio
così ottenuto e ricostruire l’immagine. Confrontare il risultato ottenuto con quelli ottenuti nei
punti A.1 e A.5.

### A.7 
Utilizzando la tecnica Half Fourier costruire il k-spazio (phase FOV = 0.6) e ricostruire
l’immagine. Confrontare il risultato con le precedenti immagini.

SOLUZIONE A

<img src="./images/z_4_2/z_4_2_img_01.png" alt="Esercitazione 4.2" style="width:100%;">

*Figura 1. Immagine ricostruita.*

<img src="./images/z_4_2/z_4_2_img_02.png" alt="Esercitazione 4.2" style="width:100%;">

*Figura 2. Immagine da parte centrale del k-spazio.*

<img src="./images/z_4_2/z_4_2_img_03.png" alt="Esercitazione 4.2" style="width:100%;">

*Figura 3. Immagine da parte esterna del k-spazio.*

<img src="./images/z_4_2/z_4_2_img_04.png" alt="Esercitazione 4.2" style="width:100%;">

*Figura 4. Immagine da sottocampionamento.*

<img src="./images/z_4_2/z_4_2_img_05.png" alt="Esercitazione 4.2" style="width:100%;">

*Figura 5. Half-Fourier. Phase FOV = 0.6.*

<img src="./images/image_es_ultima.png" alt="Esercitazione 4.2" style="width:100%;">

*Figura 6. Immagine con zero-padding.*