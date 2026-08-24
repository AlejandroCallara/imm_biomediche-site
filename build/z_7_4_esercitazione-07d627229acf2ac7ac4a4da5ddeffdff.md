# Esercitazione 7.4: Valutazione del Flusso da Immagini Phase-Contrast

La cartella “Dati per studio di flusso da immagini PC” contiene
- una serie di immagini in formato DICOM di tipo Amplitude e PhaseContrast
- Il valore $V_{scale} = \gamma A \tau = 0.81 \text{s/cm}$ ($A = \text{area del gradiente = (Tesla/cm)*s}$)

## A.1 
Selezionare
- Da un’immagine Amplitude (per es. la 16) una ROI relativa alla regione aortica, di forma e dimensioni a piacere (è possibile utilizzare un comando che permette di prendere punti/roi sull’immagine: es. `pyplot.ginput`)

Dall’header dei files PhaseContrast:
- il tempo in cui è acquisita ogni singola immagine, cioè il campo `TriggerTime`, in $\text{msec}$
- La risoluzione lungo $x$ e $y$ di ciascun pixel, cioè dal campo `PixelSpacing`, per calcolare l’area della ROI. `PixelSpacing` ha valori in $\text{mm}$.
- Lo spessore della fetta (per calcolare il volume 3D) è dato dal campo `SliceThickness`

## A.2 
Visualizzare
- La curva tempo-velocità di flusso (minima, massima e media) relativa al VOI selezionato
- la curva tempo-flusso relativa alla ROI selezionata

## SOLUZIONE

<img src="./images/z_4_5/z_4_5_img_01.png" alt="Esercitazione 4.5" style="width:100%;">

*Figura 1. Velocità.*

<img src="./images/z_4_5/z_4_5_img_02.png" alt="Esercitazione 4.5" style="width:100%;">

*Figura 2. Flusso.*
