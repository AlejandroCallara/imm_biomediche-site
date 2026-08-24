# Esercitazione 7.3: Valutazione della Perfusione da Immagini RM

<!-- Origine: Esercitazione_2025_2026_6_CALLARA_SANTARELLI.docx -->

## IMMAGINI GRADIENT-ECHO (GE) RENALI

La cartella “Dati per studio di perfusione renale” contiene una serie di immagini in formato DICOM

### B.1
Selezionare,
- dall’immagine n. 16 una ROI della regione aortica da cui ottenere $C_A(t)$ per $t = 16$. E’ possibile utilizzare il comando pyplot.ginput.
- dall’immagine n. 16 una ROI della regione renale da cui ottenere $C_T(t)$ per $t = 16$. E’ possibile utilizzare il comando pyplot.ginput.
- - il vettore dei tempi (da costruire come nell’esercitazione precedente)
B.2 Calcolare (mostrando i grafici risultanti laddove possibile)
- la curva $C_A(t)$ relativa ad una $ROI_A$ precedentemente selezionata
- la curva $C_T(t)$ relativa ad una $ROI_T$ precedentemente selezionata
- il flusso $f$ (mediante la valutazione della up-slope)

## SOLUZIONE B

<img src="./images/z_4_4/z_4_4_img_01.png" alt="Esercitazione 4.4" style="width:100%;">

*Figura. Curve tempo-concentrazione.*

Flusso stimato dalla slope: $77.81 \text{a.u./s}$
