# Esercitazione 8.5: Costruzione Immagine CSI da Segnali 13C

<!-- Origine: Esercitazione_2025_2026_9_CALLARA_SANTARELLI.docx -->

La cartella “Dati per CSI” contiene
- File DICOM *immagine_1H_FourVials* contente l’immagine 1H delle provette.
- File *DATI_13C_FourVials.mat* contenente dati 13C-MRS acquisiti mediante sequenza pulse-and-acquire, relativi a quattro provette, contenenti acqua e $^{13}C$-acetato, $^{13}C$-lattato, $^{13}C$-alanina, $^{13}C$-glicina.

Tale file contiene $256$ FID relativi a una matrice di dati $16 \times 16$. I FID di $256$ punti ciascuno sono memorizzati sequenzialmente in una matrice $256 \times 256$. Occorre fare reshape per avere i dati corretti in un tensore $16 \times 16 \times 256$. Ciascun segnale è stato acquisito $\Delta f = 5000\text{Hz}/256\text{pts}$.

A.1 
Eseguire
- La decodifica spaziale dei dati MRSI (iFFT-2D) per ciascun valore temporale dei FID.
- Il rephasing su ciascun FID (ogni FID avrà bisogno della sua correzione. Il problema è che dove non sono presenti i metaboliti fare il rephasing è complicato. Pertanto cercare soltanto tra i punti adiacenti al punto centrale dello spettro - aiuta con i FID più rumorosi).
- La stima dei parametri su ciascun FID (metodo visto nelle lezioni precedenti, con i valori iniziali dei parametri da definire). In questo caso occorre stimare i parametri di quattro picchi. (N.B. $^{13}C$-acetato e $^{13}C$-lattato hanno la stessa frequenza $f_k$, ma diverso $a_k$ e $d_k$, il numero di parametri da stimare è minore dunque). Scegliere opportunamente lower bound, upper bound e starting values.
- Mostrare le immagini CSI risultanti (rispettivamente: una per $^{13}C$-acetato e $^{13}C$-lattato, una per $^{13}C$-alanina e una per $^{13}C$-glicina).
- Ripetere i punti precedenti dopo aver eseguito uno zero padding nella decodifica spaziale (da $16 \times 16 \times 256$ a $64 \times 64 \times 256$).
- Ripetere i punti precedenti dopo aver eseguito, oltre allo zero padding nella decodifica spaziale, lo zero padding per ogni singolo FID (da $16 \times 16 \times 256$ a $64 \times 64 \times 512$).

SOLUZIONE

<img src="./images/z_4_7/z_4_7_img_01.png" alt="Esercitazione 4.7" style="width:100%;">

*Figura 1. K-spazio e Ricostruzione.*

<img src="./images/z_4_7/z_4_7_img_02.png" alt="Esercitazione 4.7" style="width:100%;">

<img src="./images/z_4_7/z_4_7_img_03.png" alt="Esercitazione 4.7" style="width:100%;">

*Figura 2. FID e spettri rifasati.*

<img src="./images/z_4_7/z_4_7_img_04.png" alt="Esercitazione 4.7" style="width:100%;">

*Figura 3. Immagini CSI.*

<img src="./images/z_4_7/z_4_7_img_05.png" alt="Esercitazione 4.7" style="width:100%;">

*Figura 4. Immagini CSI + zero padding spaziale.*
