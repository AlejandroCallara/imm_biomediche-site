# Esercitazione 7.2: Valutazione della perfusione cerebrale da immagini RM

## A. Immagini gradient-echo (GE) cerebrali

La cartella dell'esercitazione contiene:

- la cartella `Dati per studio di perfusione cerebrale`, con una serie temporale di immagini DICOM;
- lo script `BRAINVediImmagini.py` per visualizzare le immagini;
- il file `AIF.mat`, contenente nel campo `C_A` il segnale tempo-intensità arterioso, selezionato in un'arteria vicina alla regione tissutale;
- lo script di soluzione `esercitazione5_perfusione_cerebrale_svd.py`, che confronta deconvoluzione FFT, SVD troncata e regolarizzazione di Tikhonov.

### A.1 Leggere e visualizzare i dati

Ordinare i file DICOM per `InstanceNumber` e costruire la serie temporale delle immagini. Visualizzare un'immagine e ricavare dall'header:

- la sequenza di acquisizione (`ScanningSequence`);
- il tempo di eco `TE` (`EchoTime`, in ms);
- il tempo di ripetizione `TR` (`RepetitionTime`, in ms);
- l'angolo di flip (`FlipAngle`).

Costruire il vettore dei tempi usando `TriggerTime`, sottrarre il primo tempo e convertire i millisecondi in secondi. Calcolare il passo temporale $\Delta t$ come mediana delle differenze successive e verificare che il campionamento sia uniforme. I metodi seguenti assumono campioni equispaziati; se necessario, ricampionare le curve su una griglia uniforme.

### A.2 Costruire le curve tempo-concentrazione

1. Estrarre il segnale tissutale medio nella VOI definita dal codice con `vol[:, 49:51, 79:81]`: una regione di 2×2 pixel, con indici Python a partire da zero.
2. Visualizzare il segnale arterioso $S_A(t)$ e quello tissutale $S_T(t)$.
3. Selezionare i campioni pre-bolo con $t<18\,\mathrm{s}$, verificando che siano almeno tre. Per ogni curva calcolare il segnale medio pre-bolo $S_0$.
4. Convertire i segnali in curve proporzionali alla concentrazione mediante

$$
C(t)=-\frac{k}{TE}\log\left(\frac{S(t)}{S_0}\right),
$$

con $TE$ espresso in secondi e $k=1$, come nello script. Sottrarre poi la media pre-bolo della concentrazione, così da centrare il baseline a zero. Escludere segnali non positivi o conversioni non finite.

Visualizzare le curve risultanti $C_A(t)$ e $C_T(t)$.

### A.3 Stimare la risposta impulsiva con tre metodi

Il modello di perfusione è

$$
C_T(t)=(C_A*h)(t),\qquad h(t)=f\,r(t),
$$

dove $r(t)$ è la funzione residua e $f$ il flusso cerebrale (CBF). La deconvoluzione stima quindi $h(t)$, cioè la funzione residua moltiplicata per il flusso.

#### A.3.1 Deconvoluzione FFT

Calcolare

$$
\widehat h_{\mathrm{FFT}}=\frac{1}{\Delta t}\operatorname{Re}\left[\operatorname{IFFT}\left(\frac{\operatorname{FFT}(C_T)}{\operatorname{FFT}(C_A)}\right)\right].
$$

Controllare la presenza di valori non finiti e discutere l'amplificazione del rumore quando lo spettro arterioso è piccolo. Il rapporto diretto delle DFT assume una convoluzione circolare, mentre la matrice dei metodi successivi descrive una convoluzione causale: questa differenza va considerata nel confronto.

Come nello script, sovrapporre alla risposta FFT un fit esponenziale $a e^{bt}$, vincolando $a\geq0$ e $b\leq0$. Il fit è un confronto descrittivo e non sostituisce la risposta deconvoluta nel calcolo dei parametri.

#### A.3.2 Deconvoluzione mediante SVD troncata

Costruire la matrice di convoluzione causale $A$ di dimensione $N\times N$:

$$
A_{ij}=\begin{cases}\Delta t\,C_A(t_{i-j}),&i\geq j,\\0,&i<j,\end{cases}
\qquad \mathbf C_T=A\mathbf h,
$$

con indici da zero. Calcolare $A=U\Sigma V^T$ e mantenere soltanto i valori singolari $\sigma_i>0.20\,\sigma_{\max}$:

$$
\widehat{\mathbf h}_{\mathrm{TSVD}}=\sum_{\sigma_i>0.20\sigma_{\max}}\frac{\mathbf u_i^T\mathbf C_T}{\sigma_i}\mathbf v_i.
$$

Riportare quante componenti vengono mantenute e discutere l'effetto del troncamento sulla stabilità e sul picco della risposta.

#### A.3.3 Deconvoluzione con regolarizzazione di Tikhonov

Stimare la risposta minimizzando

$$
\|A\mathbf h-\mathbf C_T\|_2^2+\alpha^2\|\mathbf h\|_2^2,
\qquad \alpha=0.25\,\sigma_{\max}.
$$

Utilizzare la stessa SVD, applicando i fattori di filtro

$$
\widehat{\mathbf h}_{\mathrm{Tikh}}=V\operatorname{diag}\left(\frac{\sigma_i}{\sigma_i^2+\alpha^2}\right)U^T\mathbf C_T.
$$

Il parametro $\alpha$ di regolarizzazione è distinto dalla quantità fisiologica $\lambda$. Confrontare il filtraggio continuo di Tikhonov con il taglio netto della SVD troncata e sovrapporre le tre risposte nella VOI.

### A.4 Calcolare CBF, CBV e MTT

Per ciascun metodo stimare:

$$
\widehat f=\max_n\widehat h(t_n),\qquad
\lambda=\frac{\sum_n C_T(t_n)}{\sum_n C_A(t_n)},\qquad
MTT=\frac{\lambda}{\widehat f}.
$$

Il rapporto delle aree $\lambda$, indice del volume ematico cerebrale (CBV), è uguale per i tre metodi; CBF e MTT dipendono dalla deconvoluzione. Riportare MTT solo per $\widehat f>0$ e $\lambda>0$, altrimenti usare `NaN`.

Con questa normalizzazione $\lambda$ è adimensionale, $f$ è espresso in $\mathrm{s}^{-1}$ e MTT in secondi. Non interpretare questi risultati come valori clinici assoluti in ml/100 g/min senza le ulteriori calibrazioni e correzioni fisiologiche.

### A.5 Stimare le mappe parametriche

Ripetere l'analisi voxel per voxel nella maschera `vol[0] > 300`, usando la stessa AIF, lo stesso baseline e gli stessi parametri di regolarizzazione. Calcolare una sola volta le pseudoinverse SVD e Tikhonov e riutilizzarle per tutti i voxel.

Visualizzare CBF, $\lambda$ e MTT per i tre metodi in una griglia 3×3. Usare una scala cromatica condivisa per ciascun parametro, come nello script (percentili 2 e 98 dei valori finiti dei tre metodi). Confrontare rumore, valori estremi e distribuzione spaziale delle stime; segnalare i voxel con stime non valide.

## Soluzione

Le figure seguenti sono generate dallo script `esercitazione5_perfusione_cerebrale_svd.py` con i parametri indicati nel testo.

La serie contiene 39 immagini di 128×128 pixel; `ScanningSequence` è `EP, GR`, $TE=80\,\mathrm{ms}$, $TR=1999.996\,\mathrm{ms}$ e l'angolo di flip è $90^\circ$. Il baseline comprende 9 campioni. La SVD troncata mantiene 7 componenti su 39; per Tikhonov risulta $\alpha\simeq62.9816$.

| Parametro nella VOI | FFT | SVD troncata | Tikhonov |
|---|---:|---:|---:|
| $f$ (CBF) [$\mathrm{s}^{-1}$] | 0.058201 | 0.043936 | 0.029862 |
| $\lambda$ (CBV) | 0.239670 | 0.239670 | 0.239670 |
| MTT [s] | 4.117981 | 5.455024 | 8.025833 |

La regolarizzazione riduce il picco stimato della risposta; a parità di rapporto delle aree questo comporta un aumento di MTT. La maschera comprende 2916 voxel, di cui 228 con $\lambda\leq0$; questi ultimi non forniscono una stima fisiologicamente valida di MTT.

![Segnali arterioso e tissutale nella VOI](./images/z_7_2/sa_st.png)

*Figura 1. Segnali tempo-intensità arterioso e medio nella VOI di 2×2 pixel.*

![Curve tempo-concentrazione arteriosa e tissutale](./images/z_7_2/ca_ct.png)

*Figura 2. Curve tempo-concentrazione dopo conversione e centratura del baseline pre-bolo.*

![Risposta FFT e fit esponenziale](./images/z_7_2/r_fit.png)

*Figura 3. Risposta impulsiva stimata con FFT e fit esponenziale vincolato.*

![Confronto delle risposte FFT, SVD troncata e Tikhonov](./images/z_7_2/confronto_risposta_FFT_SVD_Tikhonov.png)

*Figura 4. Confronto delle risposte nella stessa VOI: FFT, SVD troncata e Tikhonov.*

![Confronto delle mappe CBF, lambda e MTT](./images/z_7_2/confronto_mappe_FFT_SVD_Tikhonov.png)

*Figura 5. Mappe parametriche con scala condivisa per riga: CBF, $\lambda$ e MTT; le colonne corrispondono a FFT, SVD troncata e Tikhonov.*
