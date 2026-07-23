# Esercitazione 4.1: Simulazione del Segnale RM Mediante le Equazioni di Bloch

<!-- Origine: Esercitazione_2025_2026_2_CALLARA_SANTARELLI.docx -->

## A. Descrizione temporale della precessione

### A.1 
Scrivere le seguenti funzioni in Python:

- `Rx = xrot(phi)`, che costruisce la matrice di rotazione di un angolo `phi`, espresso in radianti, attorno all’asse \(x\), e la restituisce nella variabile `Rx`.

- `Ry = yrot(phi)`, che costruisce la matrice di rotazione di un angolo `phi`, espresso in radianti, attorno all’asse \(y\), e la restituisce nella variabile `Ry`.

- `Rz = zrot(phi)`, che costruisce la matrice di rotazione di un angolo `phi`, espresso in radianti, attorno all’asse \(z\), e la restituisce nella variabile `Rz`.

- `Efp, Bfp = freeprecess(T, T1, T2, df)`, che restituisce la matrice `Efp` e il vettore `Bfp` tali che la magnetizzazione dopo la precessione libera sia data da:

  $$
  \mathbf{M}_1
  =
  \mathbf{E}_{\mathrm{fp}}\mathbf{M}
  +
  \mathbf{B}_{\mathrm{fp}}
  $$

  facendo riferimento alla formula riportata nelle diapositive.

  Utilizzare le seguenti relazioni:

  $$
  \mathbf{B}_{\mathrm{fp}}=\mathbf{B}
  $$

  $$
  \mathbf{E}_{\mathrm{fp}}
  =
  \mathbf{E}\mathbf{R}_z(\phi)
  $$

  $$
  \phi=2\pi\,df\,T
  $$

Siano: 
- $T$: durata della “free precession” in $\text{ms}$ (tempo di ‘intervallo’ dt oppure, alternativamente, tempo t, dipende da come si vuole aggiornare l’iterazione)
- $T1$ e $T2$: tempi di rilassamento in $\text{ms}$
- $df$: frequenza di risonanza in $\text{Hz}$ (off-resonance frequency)

### A.2 
Utilizzare la funzione freeprecess per un “tessuto” con $T1=600\text{ms}$, $T2= 100\text{ms}$, $df = 10^{-2}\text{kHz}$, con un valore iniziale della magnetizzazione `M=[1,0,0]` (magnetizzazione dopo impulso di 90°) e costruire un grafico con gli andamenti temporali di $M_x$, $M_y$ e $M_z$ per un tempo da $0$ a $1000\text{ms}$, con intervallo di $1\text{ms}$ (applicare cioè il sistema $M1=E*M+B$, iterativamente, con M aggiornato di volta in volta)

<img src="./images/z_4_1/z_4_1_img_01.png" alt="Esercitazione 4.1" style="width:100%;">

## B. Descrizione dell’impulso “pulse-and-acquire” e della saturazione:
Disegno dell’impulso ‘pulse-and-acquire’:

<img src="./images/z_4_1/z_4_1_img_02.jpg" alt="Esercitazione 4.1" style="width:100%;">

Quando $TR$ è breve, si ha la saturazione della magnetizzazione. Mediante questa parte di esercitazione, vediamo come, e quando, ciò avviene.

### B.1 
Dati: $T1 = 600\text{ms}$, $T2= 100\text{ms}$, $df = 0\text{Hz}$ (assi rotanti), $FA=60°$ $TR = 500\text{ms}$
Costruire un grafico che mostri gli andamenti di $M_x$, $M_y$ e $M_z$ in funzione del tempo, con $tmax = 5\text{s}$ e $dt=1\text{ms}$:

<img src="./images/z_4_1/z_4_1_img_03.png" alt="Esercitazione 4.1" style="width:100%;">

### B.2 
Ripetere B.1 modificando i seguenti parametri:

#### B.2.1 
$FA = 90°$ e $FA = 10°$ ($TR=500\text{ms}$)

<img src="./images/z_4_1/z_4_1_img_04.png" alt="Esercitazione 4.1" style="width:100%;">

#### B.2.2 
$TR = 200\text{ms}$ e $TR = 3000\text{ms}$ ($FA = 60°$)

<img src="./images/z_4_1/z_4_1_img_05.png" alt="Esercitazione 4.1" style="width:100%;">

<img src="./images/z_4_1/z_4_1_img_06.png" alt="Esercitazione 4.1" style="width:100%;">

## C. Descrizione dell’impulso Spin-Echo 
Disegno dell’impulso Spin-Echo:

<img src="./images/z_4_1/z_4_1_img_07.jpg" alt="Esercitazione 4.1" style="width:100%;">

L’impulso spin-echo consiste in un primo impulso, di $90°$ intorno all’asse $y$, e di un successivo impulso di $180°$ al tempo $TE/2$, intorno all’asse $x$. In tal modo si ha una rifocalizzazione del segnale al tempo $TE$.
### C.1
Dati $T1=600\text{ms}$, $T2= 100\text{ms}$, $df = 10^{-2}\text{kHz}$, $TR = 500\text{ms}$ e $TE = 50\text{ms}$
Costruire un grafico che mostri gli andamenti di $M_x$, $M_y$ e $M_z$ in funzione del tempo, con $tmax = 500\text{ms}$ e $dt=1\text{ms}$

(N.B. utilizzare opportunamente la funzione `freeprecess` e le matrici di rotazione `Rx` e `Ry`). 

Suddividere il tempo:
- da $0$ a immediatamente dopo l’impulso a $90°$;
- dalla fine dell’impulso a $90°$ a $TE/2$
- da $TR-TE/2$ a $TR$

<img src="./images/z_4_1/z_4_1_img_08.png" alt="Esercitazione 4.1" style="width:100%;">

### C.2 
Ripetere C.1 modificando i seguenti parametri:
$TE = 20\text{ms}$ e $TE = 70\text{ms}$

<img src="./images/z_4_1/z_4_1_img_09.png" alt="Esercitazione 4.1" style="width:100%;">

<img src="./images/z_4_1/z_4_1_img_10.png" alt="Esercitazione 4.1" style="width:100%;">

### C.3 
Valutazione del segnale con la presenza di più spin.

Considerare 10 spins con frequenze (e quindi fasi) di valore random tra $-50\text{mHz}$ e $50\text{mHz}$ (utilizzare rand) e ripetere per ciascuno spin il punto C.1. mostrare il grafico della media complessa di tutti i segnali ottenuti, in funzione del tempo ($tmax=500\text{ms}$ e $dt=1\text{ms}$).

N.B. il “segnale complesso” è dato da $S(t) = M_x(t) + 1i*M_y(t)$

<img src="./images/z_4_1/z_4_1_img_11.png" alt="Esercitazione 4.1" style="width:100%;">

Nota: questa figura può non venire sempre uguale, visto che è il risultato di realizzazioni random. Da notare però che si ha sempre il modulo del segnale più alto al tempo $TE$.

### C.4 
Ripetere C.3 modificando i seguenti parametri:

$T2 = 20\text{ms}$, $T2 = 50\text{ms}$ e $T2 = 200\text{ms}$ (“tessuti” diversi, cioè con diverso valore di $T2$)

<img src="./images/z_4_1/z_4_1_img_12.png" alt="Esercitazione 4.1" style="width:100%;">
