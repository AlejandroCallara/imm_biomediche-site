# Capitolo 6: Algoritmi Di Ricostruzione Delle Bioimmagini

<!-- Estratto da: Appunti - Principi fisici ImmaginiBiomediche.pdf, pagine 102-137 -->

<!-- Pagina PDF 102 -->

## 6.1 Introduzione

Nelle immagini tomografiche la ricostruzione avviene a partire da un insieme di dati sperimentali,
acquisiti durante l’esame al paziente, grazie all’impiego di un calcolatore per la generazione delle
immagini. I dati sono organizzati in forma matriciale, detto sinogramma, in cui sono raccolte le
proiezioni delle varie sezioni dell’immagine. Questo processo di acquisizione è descritto dalla
trasformata di Radon, la quale verrà approfondita nel paragrafo successivo. Il problema inverso
può essere risolto utilizzando algoritmi analitici come ad esempio la tecnica FBP (filtered
back_projection) oppure algoritmi iterativi. Gli algoritmi analitici differiscono da quelli iterativi
in quanto l’immagine è ricostruita direttamente dai dati ricavati dalle proiezioni senza ricorrere a
confronti tra i dati misurati ed il modello ricostruito ( ciò accade per la tecnica iterativa in cui è
necessario compiere una stima iniziale e poi paragonarla di volta in volta ai dati misurati).
Lo scopo della ricostruzione è quello di ottenere l’immagine della sezione del corpo in esame. La
ricostruzione viene fatta da un calcolatore il quale analizza le proiezioni, lungo varie direzioni,
dell’oggetto che si vuole esaminare. Successivamente, si applica un algoritmo di ricostruzione.
Quindi l’immagine ricostruita è ottenuta dalle proiezioni acquisite.
Le proiezioni vengono rappresentate in un sinogramma (*Figura 6.1*). Il sinogramma, $p_{\theta}(s)$, è una
funzione di due argomenti. È possibile visualizzarlo come immagine 2D in scala di grigi, dove s
e $\theta$ sono rispettivamente l’asse orizzontale (delle ascisse, la quale rappresenta il numero di
locazioni del rivelatore) e l’asse verticale (delle ordinate, la quale rappresenta il numero di
posizioni angolari del rilevatore). Se ad esempio, visualizziamo le proiezioni $p_{\theta}(s)$ di un impulso
di Dirac, l’immagine uscente è una sinusoide corrispondente alla funzione $s = x_0cos \theta+ y_0 sin \theta$.
Questa funzione 2D è quindi chiamata sinogramma e (quando campionate) rappresenta i dati
grezzi disponibili per la ricostruzione delle immagini. Quindi l’obiettivo della ricostruzione
tomografica è quello di stimare l’oggetto $f(x, y)$ da un sinogramma misurato. Ogni punto $(x, y)$
nello spazio oggetto, contribuisce con una sinusoide unica alla formazione del sinogramma, con
ampiezza pari $sqrt(x^2 + y^2)$ e fase della sinusoide secondo $\angle_{\pi}(x,y)$.

<img src="./images/fig_6_01_p103.png" alt="Figura pagina 103" style="width:100%;">

*Figura 6.1. Fantoccio shepp-logan e relativo sinogramma.*

Un sinogramma è la sovrapposizione di tutte queste sinusoidi, ciascuna ponderata secondo il
valore della $f (x, y)$. Quindi sembra plausibile pensare che ci siano informazioni sufficienti nel
sinogramma per recuperare l’oggetto $f$, se siamo in grado di decodificare tutte quelle sinusoidi
[1].

Poiché un sinogramma ha due coordinate ($s$ e $\theta$), che può essere visualizzato, e quindi considerato,
come un’immagine, ad esso può essere applicato qualsiasi metodo di elaborazione delle immagini
senza limitazioni. Numerosi filtri lineari e non lineari vengono applicati ai sinogrammi nel
tentativo di ridurre il rumore, di estrapolare i dati mancanti, di compensare la sfocatura del
rivelatore e/o l’attenuazione della SPECT [1].

## 6.2 Operatore di proiezione
Considerando la geometria della *Figura 6.2* dove il punto $O$ è il centro di rotazione del rivelatore,
l'angolo $\theta$ indica la posizione angolare del rivelatore e la linea D' è l'insieme dei punti M nel
campo di vista che si proietta perpendicolarmente su D, il collimatore permette soltanto ai fotoni
la cui direzione è parallela all’asse dei suoi fori di essere potenzialmente rivelati. Per ogni angolo
$\theta$ di rivelazione e per ogni posizione $s$ del rivelatore, questa direzione è definita dalla linea D’
data dall’equazione:

$$
s = x cos \theta + y sin \theta
$$

che, nella pratica individua la linea di risposta vista dal generico detettore D posto all’angolo $\theta$,
come la linea di direzione normale a $\theta$ e distante $s$ dall’origine. L'obiettivo quindi è trovare nel
campo di vista l'insieme di punti $M(x, y)$ che sono proiettati perpendicolarmente su D. Utilizzando
le usuali formule di trigonometria abbiamo che:

$$
X_I = S\cos\theta
$$

$$
Y_I = S\sin\theta
$$

e

$$
X_I - x = u\sin\theta
$$

$$
Y_I - y = -u\cos\theta
$$

combinando questi due sistemi di equazioni otteniamo

$$
x = s\cos\theta - u\sin\theta
$$

$$
y = s\sin\theta + u\cos\theta
$$

o equivalentemente

$$
s = x\cos\theta + y\sin\theta
$$

$$
u = -x\sin\theta + y\cos\theta
$$

La linea D’ è definita dall’equazione $s = x cos \theta + y sen \theta$ proiettata perpendicolarmente su D. la
linea D’ è l’insieme di punti $M(x, y)$ nel campo di vista dove i fotoni possono essere rivelati ad
una distanza $s$ quando il rivelatore è all’angolo $\theta$.

<img src="./images/fig_6_02_p104.png" alt="Figura pagina 104" style="width:100%;">

*Figura 6.2. Geometria considerata.*

## 6.3 Trasformata di Radon

Il cardine dei metodi di ricostruzione analitica è la Trasformata di Radon. Essa definisce
matematicamente l’operatore di proiezione. La trasformata di Radon $g(s, \theta)$ di una funzione $f(x,y)$, come rappresentata in Figura 6.3, è la linea integrale dei valori di f$(x, y)$, lungo la linea inclinata
ad un angolo $\theta$, dall’asse $x$ e ad una distanza $s$ dall’origine:

$$
g(s,\theta)
=
\int_{-\infty}^{\infty}
f\left(
s\cos\theta-u\sin\theta,\,
s\sin\theta+u\cos\theta
\right)\,du
$$

<img src="./images/fig_6_04_p105.png" alt="Figura pagina 105" style="width:100%;">

*Figura 6.3: proiezione di un’immagine ad un angolo $\theta$.*

Un integrale è una somma di valori, il valore di $g(s,\theta)$ è la somma dei valori $f(x,y)$ lungo la linea
D‘. Per questa ragione $g(s,\theta)$ viene chiamato ray-sums. La variabile $u$ definisce la locazione dei
punti che devono essere sommati (i punti lungo la linea D’).

Ogni punto di misura del rivelatore, per ogni angolo di proiezione è chiamato bin (elementi del
sinogramma). Quindi il numero di bins è uguale al numero dei punti di misura moltiplicato per il
numero di angoli.

La matrice mostrata in seguito rappresenta un esempio di una proiezione discreta per
un’immagine (slice) $3 \times 3$ con 2 angoli di proiezione $\theta = 0°$, $\theta = 90°$. Il valore in ogni bin è la somma dei valori dei pixels proiettati sul bin; 

esempio: $$
g_1 = f_3 + f_6 + f_9 = 2 + 2 + 3 = 7
$$. 

Il risultato della proiezione è un sinogramma con 2 righe dove i valori sono (7,9,7) e (6,9,8).

$$
F =
\begin{bmatrix}
f_1 & f_2 & f_3 \\
f_4 & f_5 & f_6 \\
f_7 & f_8 & f_9
\end{bmatrix}
\qquad
F =
\begin{bmatrix}
1 & 3 & 2 \\
6 & 1 & 2 \\
0 & 5 & 3
\end{bmatrix}
$$


dove:

$$
\begin{aligned}
g_1 &= f_3 + f_6 + f_9 = 2 + 2 + 3 = 7 \\
g_2 &= f_2 + f_5 + f_8 = 3 + 1 + 5 = 9 \\
g_3 &= f_1 + f_4 + f_7 = 1 + 6 + 0 = 7 \\
g_4 &= f_1 + f_2 + f_3 = 1 + 3 + 2 = 6 \\
g_5 &= f_4 + f_5 + f_6 = 6 + 1 + 2 = 9 \\
g_6 &= f_7 + f_8 + f_9 = 0 + 5 + 3 = 8
\end{aligned}
$$

Quindi il risultato è un sinogramma con 2 righe (corrispondenti a 2 angoli di proiezione), 3
colonne (corrispondenti a 3 punti di misura del rivelatore), con un totale di 6 bins. Da un punto di
vista matematico, l'insieme dei valori nel sinogramma e nell'immagine ricostruita possono essere
considerati come matrici o vettori. Nella seguente tabella sono elencate l'insieme di notazioni che
saranno usate nel seguito in questi appunti.

**Notazioni**

| Simbolo | Descrizione |
|---|---|
| $\mathbf{g}, \mathbf{p}$ | Vettore di proiezione |
| $\mathbf{f}$ | Vettore di immagine |
| $\mathbf{A}$ | Matrice tale che $\mathbf{g}=\mathbf{A}\mathbf{f}$ |
| $a_{ij}$ | Valore localizzato alla $i$-esima riga e alla $j$-esima colonna della matrice $\mathbf{A}$ |
| $g_i$ | Numero di rivelamenti nell’$i$-esimo bin di una proiezione |
| $m$ | Numero di pixel |
| $n$ | Numero di bin |

Considereremo sinogramma e immagine come 2 vettori; in questi vettori la localizzazione di un
bin è conosciuta come il suo indice $i$ e la localizzazione di un pixel con l'indice $j$. Si dimostra
nell'esempio che il vettore $g$ è ottenuto dal prodotto tra la matrice $A$ ed il vettore $f$.

**Esempio**

Nelle matrici illustrate nell'esempio precedente avevamo la seguente relazione tra i valori
nell’immagine e i valori nel sinogramma come mostrato in *Figura 6.4*:

$$
\begin{aligned}
g_1 &= f_3 + f_5 + f_6 \\
g_2 &= f_2 + f_5 + f_8 \\
g_3 &= f_1 + f_4 + f_7 \\
g_4 &= f_1 + f_2 + f_3 \\
g_5 &= f_4 + f_5 + f_6 \\
g_6 &= f_7 + f_8 + f_9
\end{aligned}
$$

Questo insieme di equazioni può essere espresso come un prodotto di matrice:

$$
g = A * f
$$

Questa è la formula discreta per l'operatore di proiezione; il punto essenziale è che l'operatore di
proiezione discreto può essere definito come un prodotto di matrice. $A$ è detto operatore di
proiezione. L'operatore di proiezione permette di calcolare il sinogramma da una slice. L'elemento
della matrice $a_{ij}$ può essere visto come un fattore peso, rappresentato dalla probabilità che un
fotone emesso dal pixel $j$ sia rivelato dal bin $i$.

<img src="./images/fig_6_05_p107.png" alt="Figura pagina 107" style="width:100%;">

*Figura 6.4. Principio di proiezione.*

$$
\underbrace{
\begin{bmatrix}
g_1 \\
g_2 \\
g_3 \\
g_4 \\
g_5 \\
g_6
\end{bmatrix}
}_{\mathbf{g}}
=
\underbrace{
\begin{bmatrix}
0 & 0 & 1 & 0 & 1 & 1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 & 1 & 0 & 0 & 1 & 0 \\
1 & 0 & 0 & 1 & 0 & 0 & 1 & 0 & 0 \\
1 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 1 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 1
\end{bmatrix}
}_{\mathbf{A}}
\underbrace{
\begin{bmatrix}
f_1 \\
f_2 \\
f_3 \\
f_4 \\
f_5 \\
f_6 \\
f_7 \\
f_8 \\
f_9
\end{bmatrix}
}_{\mathbf{f}}
$$

$$
g_i
=
a_{i1}f_1+a_{i2}f_2+\cdots+a_{im}f_m
=
\sum_{j=1}^{m}a_{ij}f_j
$$

L'uso di zeri o uni nella matrice $A$ possono essere interpretati come la scelta binaria che un pixel
determinato contribuisce o non contribuisce al numero di conteggi rivelati in ogni bin. Noi
comunque vorremmo trovare un modello più realistico che deve essere capace di modulare questo
contributo.
Facendo così, gli elementi $a_{ij}$ non possono essere necessariamente uguali a 0 o 1, ma possono
essere valori reali tra 0 e 1. I valori sono scelti attentamente per prendere in considerazione la
geometria di acquisizione e, più precisamente, il fatto che una frazione variabile di un pixel
contribuisce ai rivelamenti acquisiti in un dato bin, dipende dalle loro posizioni relative e
dall'angolo di acquisizione.

Teoricamente esistono dei metodi diretti per risolvere il sistema di equazioni, come $g = Af$. Un
metodo diretto consiste nella determinazione della matrice inversa $A^{-1}$ poiché $f = A^{-1} g$. 

Questo metodo potrebbe avere molti difetti:
- È computazionalmente intensivo per i computer attuali, anche per immagini $64 \times 64$;
- $A^{-1}$ potrebbe non esistere;
- $A^{-1}$ potrebbe non essere unica;
- $A^{-1}$ potrebbe essere mal posta, cioè piccoli cambiamenti nei dati $g$ potrebbero produrre
molte differenze nel risultato $f$, per esempio, quando $g$ è rumorosa.

Sfortunatamente, in pratica, la matrice $A^{-1}$ è mal posta, a causa del rumore nelle proiezioni.
La trasformata di Radon è la base che permette di descrivere diverse tecniche tomografiche usate
in medicina quali la tomografia trasmissiva (TAC), la tomografia emissiva (PET, SPECT). [2]

## 6.4 Operatore di Retroproiezione

La trasformata di Radon rappresenta un oggetto bidimensionale f(x,y) in un sinogramma $g(s,\theta)$,
composto di integrali di linea attraverso l’oggetto. Un approccio per recuperare l’oggetto dal
sinogramma sarebbe quello di prendere ogni valore del sinogramma e “distribuirlo” indietro lungo
tutta la direzione del raggio che l’ha prodotta come mostrato in *Figura 6.5*. Quindi è possibile
ottenere un oggetto sul piano $(x, y)$ a partire da informazioni che invece si riferiscono allo spazio
$s, \theta$ delle proiezioni. Questo tipo di operazione è chiamata retroproiezione ed è fondamentale per
la ricostruzione delle immagini tomografiche.

<img src="./images/fig_6_07_p109.png" alt="Figura pagina 109" style="width:100%;">

<img src="./images/fig_6_08_p109.png" alt="Figura pagina 109" style="width:100%;">

*Figura 6.5: (sopra) schema proiezione; (sotto) schema retroproiezione*

L'operatore di retroproiezione è definito come:

$$
b(x,y)
=
\int_{0}^{\pi} g(s,\theta)\,d\theta
$$

La retroproiezione rappresenta l’accumulo dei ray-sums di tutti i raggi che passano attraverso
ogni punto $M(x,y)$. Come visto nei paragrafi precedenti $s$ è data dall’equazione:

$$
s = xcos \theta + ysin \theta
$$

In condizioni ideali (in particolare senza rumore), le proiezioni acquisite tra gli angoli $\pi$ e $2\pi$ non
forniscono nuove informazioni, perché sono solamente i simmetrici delle proiezioni acquisite tra
gli angoli $0$ e $\pi$. Sostituendo l’integrale della proiezione con una somma abbiamo:

$$
b(x,y)
=
\sum_{k=1}^{p}
g(s_k,\theta_k)\,\Delta \theta
$$

Dove $p$ indica il numero di proiezioni acquisite, $\theta _k$ è la k-esima posizione angolare del rivelatore,
$s$ è la locazione lungo il rivelatore e $\Delta \theta$ è il passo angolare tra 2 successive proiezioni $(\Delta \theta = \pi/p)$.
L’obiettivo è cercare $b(x, y)$ che è il risultato della retroproiezione al punto $M(x, y)$. Per ogni
angolo $\theta _k$ usando l’equazione $s = xcos \theta + ysin \theta$ viene cercata la posizione $s$ (sul rilevatore),
cioè la posizione della proiezione sul punto $M(x, y)$, aggiungendo il valore $g(s_k, \theta _k)$ al valore
corrente di $M(x, y)$, il cui valore iniziale deve essere $0$.
Questo processo viene ripetuto per tutti gli angoli e, la somma viene divisa per il numero delle
proiezioni angolari. Un esempio, semplice, di retroproiezione è mostrato in *Figura 6.6* [2].

<img src="./images/fig_6_10_p110.png" alt="Figura pagina 110" style="width:100%;">

*Figura 6.6 : retroproiezione di un sinogramma*

**Retroproiezione di un sinogramma 2 x 3**

Il valore in ogni pixel è la somma dei valori dei bins che, dato un angolo di rivelamento, può
ricevere fotoni da quel pixel ed è diviso dal numero di righe del sinogramma.
Esempio:
$$
f_1 = (g_3 + g_4)/2 = (7 + 6)/2 = 6,5
$$

Il metodo della retroproiezione è esemplificato nella *Figura 6.5*, dove è proposta la ricostruzione di
un oggetto rettangolare, tramite due sue proiezioni. Per un set limitato di angoli, immagini distinte
possono produrre le stesse proiezioni.
Esempio: Due immagini distinte che possono avere la stessa proiezione all'angolo $0$:


Immagine 1:

$$
\begin{bmatrix}
2 & 0 & 5 \\
4 & 3 & 1 \\
0 & 1 & 1
\end{bmatrix}
$$

Immagine 2:

$$
\begin{bmatrix}
1 & 0 & 2 \\
5 & 4 & 0 \\
0 & 0 & 5
\end{bmatrix}
$$

Somma delle righe della prima matrice:

$$
\begin{aligned}
2 + 0 + 5 &= 7 \\
4 + 3 + 1 &= 8 \\
0 + 1 + 1 &= 2
\end{aligned}
$$

Somma delle colonne della prima matrice:

$$
\begin{aligned}
2 + 4 + 0 &= 6 \\
0 + 3 + 1 &= 4 \\
5 + 1 + 1 &= 7
\end{aligned}
$$

Somma delle righe della seconda matrice:

$$
\begin{aligned}
1 + 0 + 2 &= 3 \\
5 + 4 + 0 &= 9 \\
0 + 0 + 5 &= 5
\end{aligned}
$$

Somma delle colonne della seconda matrice:

$$
\begin{aligned}
1 + 5 + 0 &= 6 \\
0 + 4 + 0 &= 4 \\
2 + 0 + 5 &= 7
\end{aligned}
$$

Da queste due immagini possiamo avere la stessa proiezione all'angolo $0$. Questo illustra il fatto
che quando abbiamo un numero insufficiente di proiezioni, la soluzione finale potrebbe essere
sbagliata. Quindi, teoricamente, è richiesto un numero infinito di proiezioni per perfezionare la
ricostruzione dell'immagine finale, altrimenti potremmo avere degli artefatti.
In *Figura 6.7A*, è rappresentata l'immagine da ricostruire e le *Figure 6.7 B-G*, rappresentano le
ricostruzioni ottenute con un diverso numero di proiezioni con una diversa visibilità degli artefatti.
Gli artefatti possono essere ridotti, aumentando il numero di proiezioni acquisite.

<img src="./images/fig_6_11_p112.png" alt="Figura pagina 112" style="width:100%;">

*Figura 6.7. Illustrazione dell’artefatto a stella: (A) fetta usata per la creazione delle proiezione; (B_G) 1, 3, 4, 16, 32, e 64 proiezioni equamente distribuite su 360° sono usate per ricostruire l’immagine utilizzando gli algoritmi di retroproiezione.*

Purtroppo, nella sua forma più semplice, questa procedura non consente di ripristinare l’oggetto
$f(x, y)$, ma produce invece una versione sfocata dell’oggetto $f_b(x, y)$, come mostrato in *Figura 6.8*.
Questa versione sfocata è chiamata Laminogramma [1].

Il punto principale di questa parte è quindi che l'operatore di retroproiezione non è esattamente
l'inverso dell'operatore di proiezione. Questo problema è dovuto al fatto che durante il processo
di retroproiezione, ogni valore del bin è attribuito a tutti i pixel che proiettano su quel bin, con lo
stesso peso.
In particolare, quando il sinogramma di un oggetto asimmetrico è corrotto dal rumore, è
ipotizzabile che diversi punti di vista avranno segnale diverso in base ai coefficienti del rumore.
Pertanto, si analizzano le seguenti operazioni di proiezione angolarmente-pesati:

$$
f_b(x,y)
=
\int_{0}^{\pi}
k(\theta)\,
p_{\theta}\!\left(x\cos\theta+y\sin\theta\right)
\,d\theta
$$

dove $k(\theta)$ denota il peso scelto dall’utente per l’angolo $\theta$.

<img src="./images/fig_6_12_p113.png" alt="Figura pagina 113" style="width:100%;">

*Figura 6.8:. Rappresentazione di un Laminogramma (retroproiezione non filtrata). In figura: $r=s$, $\phi = \theta$.*

Il teorema seguente mostra che il laminogramma $f_b(x, y)$ è una versione molto offuscata
dell’oggetto originale $f(x, y)$:


**Teorema**: se $p_\theta(s)$ rappresenta la trasformata di Radon della funzione $f(x,y)$ e $f_b(x, y)$
indica la retroproiezione angolarmente-pesata di $p_\theta (s)$, quindi:

$$
f_b(x,y)
=
h(s,\theta)\otimes f(x,y)
$$

dove

$$
h(s,\theta)
=
\frac{
k\!\left(\left(\theta+\frac{\pi}{2}\right)\bmod \pi\right)
}{
|s|
}
$$

Per la dimostrazione si rimanda a [1].

Nel caso consueto in cui $k(\theta) = 1$ vediamo che la (29) produce un risultato che è l’oggetto originale
sfocato dalla funzione $1/s$. Questa forma di PSF (Point Spread Function: risposta all’impulso) ha
le estremità molto pesanti tale da avere un laminogramma quasi inutile per l’interpretazione
visiva. La *Figura 6.9* illustra la funzione $1/s$.


Poiché il laminogramma $f_b(x, y)$ è l’oggetto $f(x, y)$ convoluto con la PSF $h(s, \theta)$ in (29), ne segue
che nel dominio delle frequenze abbiamo

$$
F_b(\omega,\theta)
=
H(\omega,\theta)\,F_0(\omega,\theta)
$$

<img src="./images/fig_6_13_p114.png" alt="Figura pagina 114" style="width:100%;">

*Figura 6.9. Illustrazione della funzione $1/s$ e la sua "estremità pesante".*

Dove $H(ω, \theta)$ indica la forma polare della FT 2D di $h(s,\theta)$.

Il teorema seguente generalizza tale risultato al caso angolarmente ponderato.

**Teorema:** la PSF data nella (29) ha la seguente trasformata di Fourier TF bidimensionale
per $\theta \quad [0,\pi]$ e $\omega \in \mathbb{R}$:

$$
h(s,\theta)
=
\frac{1}{|s|}
\,k\!\left(\left(\theta+\frac{\pi}{2}\right)\bmod \pi\right)
\quad \Longleftrightarrow \quad
H(\omega,\theta)
=
\frac{1}{|\omega|}\,k(\theta)
$$

Per la dimostrazione si rimanda a [1].

Così la relazione della frequenza spaziale tra il laminogramma e l’oggetto originale è:

$$
F_b(\omega,\theta)
=
\frac{k(\theta)}{|\omega|}
\,F_0(\omega,\theta)
$$

le alte frequenze spaziali sono fortemente attenuate dal termine $1/|\omega|$, questo spiega perchè il
laminogramma risulta molto sfocato. Comunque la relazione (33) suggerisce un metodo di
deconvoluzione per il recupero di $f(x, y)$ da $f_b(x, y)$.

## 6.5 Teorema della Sezione Centrale

Lo schema in *Figura 6.10* suggerisce l’esistenza di una relazione tra la trasformata di Radon e la
trasformata di Fourier della $f(x, y)$. Questo legame fornisce uno strumento utile per invertire la
trasformata di Radon stessa.
Questo legame è dato dal Teorema della Sezione Centrale, il quale può essere enunciato come
segue:

**Teorema:** la Trasformata di Fourier di una proiezione $P_{\theta}(s)$ ottenuta ad un angolo $\theta$
rispetto all’asse $x$, coincide con la trasformata di Fourier $F(u, v)$ della $f(x, y)$ calcolata
lungo una retta nel piano $(u, v)$, che forma un angolo $\theta$ con l’asse $u$ (vedi schema).

In forma più compatta possiamo dire:
se $F(u, v)$ indica la trasformata di Fourier di $f(x, y)$ e $P_{\theta}(\omega)$ indica la trasformata di Fourier della
proiezione $p_{\theta} (s)$, possiamo scrivere:

$$
F(\omega, \theta) = P_{\theta}(\omega)
$$

dove: $u = \omega cos\theta$ e $v = \omega sin \theta$.

Quindi conoscere la trasformata di Radon di un oggetto equivale a conoscere la sua trasformata
di Fourier.


Definiamo $F(u, v)$, $P_{\theta} (\omega)$:

$$
F(u,v)
=
\int_{-\infty}^{\infty}
\int_{-\infty}^{\infty}
f(x,y)\,
e^{-i2\pi(ux+vy)}
\,dx\,dy
$$

$$
P_{\theta}(\omega)
=
\int_{-\infty}^{\infty}
p_{\theta}(r)\,
e^{-2\pi i\omega r}
\,dr
$$

Segue:

$$
P_{\theta}(\omega)
=
F\!\left(\omega\cos\theta,\omega\sin\theta\right)
=
F_0(\omega,\theta),
\qquad
\forall\,\omega\in(-\infty,\infty),
\quad
\theta\in[0,\pi]
$$


<img src="./images/fig_6_17_p116.png" alt="Figura pagina 116" style="width:100%;">

*Figura 6.10. Rappresentazione del teorema della sezione centrale. In figura: $t=s$ e $S=P$.*

Quindi la trasformata di Radon descrive completamente qualsiasi oggetto $f(x, y)$, poiché c’è una
corrispondenza uno a uno tra la trasformata di Radon e la trasformata di Fourier bidimensionale
$F(u, v)$, e dalla $F(u, v)$ possiamo recuperare $f(x, y)$ dalla trasformata inversa di Fourier 2D.

## 6.6 Tecniche di ricostruzione analitiche

Manipolando le espressioni derivate nelle sezioni precedenti, si possono trovare diversi metodi
per invertire la Trasformata di Radon e quindi per ottenere l’immagine f(x,y) a partire dalle sue
proiezioni $g(s,\theta)$ (o $p_{\theta} (s)$ ). La ricostruzione della sezione tomografica a partire dai dati rivelati è
quindi, dal punto di vista matematico, un problema inverso.
Tutte le tecniche tomografiche usate nell’imaging medico (TAC, PET, SPECT, MRI....) hanno in
comune il fatto di richiedere la risoluzione di un problema inverso, cioè dal passaggio dei dati
acquisiti alla distribuzione puntuale della grandezza che descrive la sezione corporea.
Questo paragrafo descrive tre alternative: la ricostruzione diretta di Fourier basata sul teorema
della sezione centrale, il metodo backproject-filter (BPF) basato sul laminogramma, il metodo
della Convolve-Backproject (CBP), chiamato anche metodo filter-backproject (FBP). Ciascuno
di questi metodi utilizza alcune delle relazioni di *Figura 6.11*.
In questa trattazione considereremo la versione ideale del problema tomografico in cui sono
disponibili le intere proiezioni continue. Nella pratica invece, si ha solo un insieme discreto di
proiezioni e raggi.

<img src="./images/fig_6_18_p117.png" alt="Figura pagina 117" style="width:100%;">

*Figura 6.11. Relazione tra un oggetto bidimensionale f(x, y) e le sue trasformate e proiezioni. La parte
sinistra della figura è il dominio dell'immagine, la parte destra è il dominio della proiezione. L’anello
interno è dominio dello spazio, l’anello esterno è nel dominio della frequenza. In figura: $\phi = \theta$, $r=s$, $\nu = \omega$.*


### 6.6.1 Ricostruzione Diretta di Fourier

Il metodo di ricostruzione diretta di Fourier si basa direttamente sul teorema della sezione
centrale. Per ricostruire l’immagine bidimensionale $f(x, y)$ dalla $p_{\theta}(s)$ con il metodo diretto di
Fourier, si eseguono i seguenti passi:

-Si prende la FT 1D di ciascuna proiezione $p_{\theta}(s)$ per ottenere $P_{\theta}(\omega)$ (trasformata di Fourier di ogni proiezione) per ogni angolo $\theta$;
- Si crea una rappresentazione polare $F_0(\omega, \theta)$ della FT bidimensionale di un oggetto $F(u, v)$ utilizzando il teorema della sezione centrale: $F_0(\omega, \theta) = P_{\theta}(\omega)$;
- Si converte la rappresentazione polare $F_0(\rho,\theta)$ in coordinate cartesiane $F(u,v)$. Questo approccio fu "il primo metodo applicabile per la ricostruzione delle immagine dalle loro proiezioni"; Per i dati campionati, questo passaggio dal polare al cartesiano, spesso chiamato gridding, richiede un interpolazione molto accurata. La figura 12
illustra il processo.
- Si calcola la trasformata inversa di $F(uv)$ per ottenere la $f(x,y)$. In pratica questo passaggio viene implementato utilizzando la FFT 2D inversa che richiede campioni in coordinate cartesiane, mentre la relazione $F_0(\omega, \theta) = P_{\theta}(\omega)$ è intrinsecamente polare. Da qui la necessità dell’interpolazione.

Questo metodo potrebbe funzionare perfettamente se i dati venissero forniti senza rumore e se le
proiezioni $p_{\theta}(s)$ fossero continue. Gli svantaggi di questo metodo nascono dalle richieste di un
gran numero di FT e dal gridding che può causare diversi artefatti di interpolazione.

<img src="./images/fig_6_19_p118.png" alt="Figura pagina 118" style="width:100%;">

*Figura 6.12: illustrazione di campioni in coordinate polari interpolati in campioni di coordinate cartesiane.*

### 6.6.2 Metodo backproject-filter (BPF)

Un altro metodo di ricostruzione è suggerita dalla relazione di Fourier (2) tra il laminogramma e
l’oggetto originale. Risolvendo la (2) per la FT 2D dell’oggetto si ottiene:

$$
F(u,v)
=
\frac{\sqrt{u^2+v^2}}
{k\!\left(\angle_{\pi}(u,v)\right)}
\,F_b(u,v)
$$

dove $F_b(u, v)$ indica la FT bidimensionale del laminogramma, la fase è così definita:

$$
\angle_{\pi}(u,v)
=
\begin{cases}
\tan^{-1}\!\left(\dfrac{v}{u}\right), & uv>0 \\[6pt]
0, & v=0 \\[6pt]
\dfrac{\pi}{2}, & u=0,\ v\neq 0 \\[6pt]
\tan^{-1}\!\left(\dfrac{v}{u}\right)+\pi, & uv<0
\end{cases}
$$

Il filtro con risposta in frequenza pari a $|\omega| = \sqrt{v^2 + u^2}$ è chiamato filtro conico per la sua forma.

I passi del metodo BPF sono i seguenti:
- Si sceglie una funzione non_nulla $k(\theta)$;
- Si esegue la retroproiezione $\theta$-pesata del sinogramma $p_{\theta}(s)$ per formare il laminogramma
$f_b(x, y)$ usando la (28);
- Si calcola la FT 2D di $f_b(x, y)$ per ottenere $F_b(u, v)$;
- Si applica il filtro conico nel dominio di Fourier usando la (38);
- Si calcola l’inverso della FT 2D $F(u,v)$ per ottenere $f(x,y)$.

Il filtro conico annulla la componente DC di $f(x, y)$. Questa componente può essere recuperata
utilizzando la proprietà di conservazione del volume della trasformata di Radon, (vedi appendice
A);

Questo approccio è chiamato metodo back-project filter (BPF) perché in primo luogo si procede
con la retroproiezione del sinogramma e poi si applica il filtraggio con il filtro conico per
"deconvolvere" l’effetto $1/|\rho|$ della retroproiezione.
Nella pratica, utilizzando il filtro conico senza ulteriori filtraggi si potrebbe amplificare
eccessivamente il rumore ad alta frequenza. Per controllare il rumore, il filtro è di solito apodizzato nel dominio delle frequenze con una funzione a finestra. In particolare considereremo la seguente espressione:

$$
F(u,v)
=
A(u,v)\,
\frac{\sqrt{u^2+v^2}}
{k\!\left(\angle_{\pi}(u,v)\right)}
\,F_b(u,v)
$$

dove $A(u, v)$ è un filtro passa basso. In assenza di rumore, l’immagine risultante ricostruita
soddisfa:

$$
\hat{f}(x,y)
=
a(x,y)\otimes f(x,y)
$$

dove $a(x, y)$ è la trasformata inversa di $A(u, v)$.

Una difficoltà pratica utilizzando il metodo di ricostruzione BPF è che il laminogramma $f_b(x,y)$
ha valori su un piano infinito (anche per un oggetto $f$ finito) a causa della coda della risposta $1/|s|$
in (29). In pratica, il piano su cui è definito $f_b(x,y)$ deve essere troncato ad una dimensione finita ai
fini dell’archiviazione informatica, tale troncamento può causare problemi nella deconvoluzione.
Inoltre, utilizzando la FFT bidimensionale per applicare i risultati del filtro conico nella
convoluzione periodica, si possono ottenere effetti di sovrapposizione (“wrap-around”) a causa
della natura passa-alto del filtro conico. Per ridurre al minimo gli artefatti dovuti al troncamento
spaziale e alla convoluzione periodica, va valutata $f_b(x,y)$ numericamente su una griglia di valori
che è notevolmente più grande della dimensione dell’oggetto $f(x, y)$. Una griglia con molti valori
aumenta i costi computazionali sia del passo di retroproiezione che delle operazioni 2D FFT
utilizzate per il filtro conico. Il metodo di ricostruzione FBP, descritto più avanti, supera
largamente questa limitazione.
Il metodo FBP ha il vantaggio di richiedere solo trasformate di Fourier 1D, mentre il metodo
diretto di Fourier e il metodo BPF richiedono le trasformate di Fourier bidimensionali.

### 6.6.3 Metodo filter-backproject (FBP)

Dal paragrafo precedente, abbiamo visto che applicando una retroproiezione senza filtro ciò che
si ottiene è un laminogramma sfocato che deve essere necessariamente deconvoluto da un filtro
conico per ottenere l’immagine originale.
I passi da eseguire sono:

<img src="./images/fig_6_20_p120.png" alt="Figura pagina 120" style="width:100%;">

Poichè le prime due operazioni godono delle proprietà di linearità e di shift-invarianza, in linea
di principio si potrebbe spostare il filtro conico in cima alle operazioni in modo da ottenere un
risultato complessivo uguale, seguendo la seguente relazione:

<img src="./images/fig_6_21_p121.png" alt="Figura pagina 121" style="width:100%;">

In cui l’oggetto filtrato $\tilde{f}(x,y)$, assumendo $k(\theta) = 1$, ha il seguente spettro:

$$
\tilde{F}(ω,\theta)= |\omega|F_0(\omega,\theta)
$$

Naturalmente, nella pratica, non si può filtrare l’oggetto prima di acquisire le sue proiezioni.
Tuttavia, applicando il teorema della sezione centrale di Fourier alla (42), vediamo che ogni
proiezione ha la seguente trasformata di Fourier 1D:

$$
\tilde{p}_{\theta}(s)
\;\xleftrightarrow{\mathrm{FT}}\;
\tilde{P}_{\theta}(\nu)
=
\left.\tilde{F}(\omega,\theta)\right|_{\omega=\nu}
=
\left.|\omega|\,F_0(\omega,\theta)\right|_{\omega=\nu}
=
|\nu|\,F_0(\nu,\theta)
=
|\nu|\,P_{\theta}(\nu)
$$

Questa relazione indica che possiamo sostituire il filtro conico 2D con una serie di filtri 1D con
risposta in frequenza $|\nu|$ applicata ad ogni proiezione $p_{\theta}(·)$. Questo tipo di filtro è chiamato filtro
a Rampa per la sua forma. Lo schema a blocchi diventa:

<img src="./images/fig_6_22_p121.png" alt="Figura pagina 121" style="width:100%;">

Questo approccio di ricostruzione è chiamato metodo di filter-backproject (FBP), ed è il più usato
e diffuso in tomografia.
Una descrizione formale del metodo FBP si ottiene utilizzando il teorema della sezione centrale
di Fourier come segue:

$$
\begin{aligned}
f(x,y)
&=
\iint
F(u,v)\,
e^{i2\pi(xu+yv)}
\,du\,dv
\\[4pt]
&=
\int_{0}^{\pi}
\int_{-\infty}^{\infty}
F(\omega\cos\theta,\omega\sin\theta)\,
e^{i2\pi\omega(x\cos\theta+y\sin\theta)}
\,|\omega|\,d\omega\,d\theta
\\[4pt]
&=
\int_{0}^{\pi}
\int_{-\infty}^{\infty}
P_{\theta}(\omega)\,
e^{i2\pi\omega(x\cos\theta+y\sin\theta)}
\,|\omega|\,d\omega\,d\theta
\\[4pt]
&=
\int_{0}^{\pi}
\tilde{p}_{\theta}
\left(
x\cos\theta+y\sin\theta
\right)
\,d\theta
\end{aligned}
$$

In cui la proiezione filtrata $p_{\theta}(s)$ viene definita:

$$
\tilde{p}_{\theta}(s)
=
\int_{-\infty}^{\infty}
P_{\theta}(\omega)\,|\omega|\,
e^{i2\pi\omega s}
\,d\omega
$$

I passi del metodo FBP possono essere riassunti come segue:
- Per ogni angolo di proiezione $\theta$, si calcola la FT 1D delle proiezioni $p_{\theta}(s)$ per ottenere
$P_{\theta}(\omega)$;
- Si moltiplica $P_{\theta}(\omega)$ per $|\omega|$ (filtro a rampa);
- Per ogni $\theta$ si calcola la trasformata inversa di Fourier 1D di $|\omega|P_{\theta}(\omega)$ per ottenere la
proiezione filtrata $\tilde{p}_{\theta}(s)$. Nella pratica questo filtro è spesso fatto utilizzando una
FFT, che produce una convoluzione periodica. Poiché il dominio spaziale del Kernel
(nucleo) corrispondente a $|\omega|$ non è spazio-limitato, la convoluzione periodica può causare
artefatti. Questi artefatti possono essere evitati con lo zeropadding applicato al
sinogramma. Il non corretto campionamento del filtro a rampa può inoltre causare un
artefatto di aliasing;
- si esegue l’operazione di retroproiezione descritta in (28) sul sinogramma filtrato per
ottenere la $f(x,y)$ vale a dire:
- $$
f(x,y)
=
\int_{0}^{\pi}
\tilde{p}_{\theta}
\left(
x\cos\theta+y\sin\theta
\right)
\,d\theta
$$

Il filtro a rampa annulla la componente DC di ogni proiezione. Se lo si desidera, questa può essere
ripristinata utilizzando la proprietà di conservazione di volume;

#### Retroproiezione Filtrata versus Retroproiezione non filtrata ####
Ricordiamo che una retroproiezione non filtrata di un sinogramma dà un’immagine sfocata da
$1/|s|$. Questa sfocatura è dovuta al fatto che i valori della proiezione (sono tutti non_negativi) "si
accumulano"“" nel laminogramma, e non c’è alcuna interferenza distruttiva.
Al contrario, dopo aver filtrato con filtro a rampa, le proiezioni hanno valori sia positivi che
negativi, cosi si possono verificare interferenze distruttive, che è sperabile avvengano nelle
regioni dell’immagine con valori uguali a zero. La *Figura 6.13* mostra con un esempio questo
concetto.

<img src="./images/fig_6_23_p123.png" alt="Figura pagina 123" style="width:100%;">

*Figura 6.13. Metodo FBP. sopra: un oggetto quadrato $f(x,y)$, il suo sinogramma $p_{\theta}(s)$ e il suo
laminogramma $f_b(x,y)$. Sotto: sinogramma filtrato $p_{\theta}(s)$ e l’immagine back-projected. Grazie al
filtro a rampa i dettagli del quadrato sono preservati.*

### 6.6.4 Metodo Convolve- backproject (CBP)

Il filtro a rampa amplifica il rumore ad alte frequenze, quindi nella pratica lo si deve apodizzare
con un filtro passa-basso 1D $A(\omega)$, in questo caso la (45) viene sostituita da:

$$
\tilde{p}_{\theta}(s)
=
\int_{-\infty}^{\infty}
P_{\theta}(\omega)\,
A(\omega)\,
|\omega|\,
e^{i2\pi\omega s}
\,d\omega
$$

In alternativa, si può effettuare questa operazione di filtro nel dominio spaziale attraverso una
convoluzione radiale:

$$
\tilde{p}_{\theta}(s)
=
p_{\theta}(s)\otimes h_a(s)
=
\int
p_{\theta}(s')\,
h_a(s-s')\,
ds'
$$

Dove il kernel del filtro $h(s)$ è la trasformata inversa di Fourier $H_a(\omega) = A(\omega)|\omega|$, cioè

$$
h_a(s)
=
\int_{-\infty}^{\infty}
A(\omega)\,|\omega|\,
e^{i2\pi\omega s}
\,d\omega
$$

Combinando l’espressione (49) con la (46) e la (47) otteniamo il seguente metodo di Convolve-
backproject:

$$
\begin{aligned}
f(x,y)
&=
\int_{0}^{\pi}
\left(p_{\theta}\otimes h_a\right)
\left(x\cos\theta+y\sin\theta\right)
\,d\theta
\\[4pt]
&=
\int_{0}^{\pi}
\int_{-\infty}^{\infty}
p_{\theta}(s)\,
h_a\left(x\cos\theta+y\sin\theta-s\right)
\,ds\,d\theta
\end{aligned}
$$

Sebbene il kernel di convoluzione $h_a(s)$ di solito non è spazio-limitato, l’oggetto (e quindi le sue
proiezioni) sono spazio limitato. In questo modo la convoluzione diventa fattibile. D’altra parte
la convoluzione nel dominio spaziale richiede più calcoli rispetto alle implementazioni nel
dominio delle frequenze con il metodo FFT, motivo per cui il metodo FBP è preferito al "cugino"
CBP.

## 6.7 Tecniche di ricostruzione iterative

Le tecniche di ricostruzione analitiche sfruttano le importanti informazioni fornite da una serie di
teoremi e trasformate che vengono sfruttate al fine di risolvere il problema inverso alla proiezione,
ovvero la ricostruzione di un’immagine tomografica. Queste tecniche, come abbiamo visto,
risultano essere particolarmente potenti ed efficaci da un punto di vista teorico, come nel caso del
teorema della sezione centrale, e presentano alcuni evidenti vantaggi operativi come ad esempio
la rapidità di calcolo dell’immagine ricostruita. Tuttavia esistono degli aspetti negativi che non
possono essere trascurati, come la necessità di avere un numero elevato di proiezioni su cui
lavorare e la presenza di caratteristici artefatti da ricostruzione. L’esigenza di una valida
alternativa ha portato nel corso degli ultimi decenni allo sviluppo di un approccio più informatico
alla soluzione del problema. Tali metodologie sono comunemente conosciute in letteratura come
metodi iterativi.
I metodi iterativi più utilizzati riguardano gli algoritmi ART (Algebraic Reconstruction
Techniques), le tecniche di minimizzazione dell’errore quadratico medio tipiche dei metodi LS
(least squares, ovvero ai minimi quadrati) e i metodi di massima verosimiglianza (maximum
likehood).

Occorre notare che in questo paragrafo e nei successivi verranno descritti tali algoritmi per dati
TAC che sfruttano le proprietà di interazione tra i tessuti e i raggi x; tuttavia, tali metodi iterativi
(come anche gli analitici) sono utilizzabili, ed utilizzati, anche su dati ottenuti da altre metodiche
di imaging , quali la SPECT, PET e, più raramente, MRI.

### 6.7.1 Il modello geometrico

Quasi tutti i metodi iterativi utilizzano un modello geometrico per rappresentare i dati delle
proiezioni che consente in prima analisi la discretizzazione di una struttura reale, ovvero la
sezione in esame, in dati discretizzati. La nostra immagine tomografica, frutto di un processo di
ricostruzione, rappresenta una sezione volumetrica riferita ad un volume totale, ovvero il corpo
del paziente. Questa sezione bidimensionale è definita sul piano $(x,y)$ e rappresenta la
sovrapposizione delle strutture contenute lungo un certo spessore che caratterizza la sezione,
definito sull’asse $z$. Minore sarà questo spessore, migliore sarà la risoluzione spaziale lungo tale
direzione. Ogni immagine da ricostruire viene considerata suddivisa in un certo numero di
volumetti detti voxel , il cui spessore dipende proprio dalla risoluzione spaziale lungo l’asse $z$.
Ad ogni voxel, corrispondente ad una precisa porzione di tessuto individuata da una coppia di
coordinate sul piano $(x,y)$, viene attribuito un certo valore relativo al coefficiente di attenuazione
lineare, nel caso di immagini TAC.

Descriviamo ora una rappresentazione algebrica delle proiezioni in relazione alla dimensione
della cella elementare, allo spessore del raggio x e alla porzione dello stesso che attraverserà la
cella. A fini semplificativi utilizziamo un modello geometrico a fasci paralleli (parallel beam) con
un numero di emettitori pari al numero di detettori. Nel caso di utlizzo di fasci conici (fan beam)
sono necessarie ulteriori elaborazioni sui dati acquisiti, che tralasciamo.

<img src="./images/fig_6_24_p126.png" alt="Figura pagina 126" style="width:100%;">

*Figura 6.14.*

Consideriamo il raggio x con spessore pari al lato del voxel e il valore p della proiezione sarà dato
dalla somma dei contribuiti di ciascun voxel lungo una certa direzione (definita dall’angolo di
proiezione) e dalla frazione di area di ciascun voxel che il raggio andrà attraversare:

$$
p_i = \sum_{j=1}^{n} w_{ij} f_j,
\qquad
i = 1,2,\ldots,m
$$

Dove $m$ è il numero totale dei raggi e $w_{ij}$ è il coefficiente della matrice dei pesi che indica la
frazione di area del voxel $j$ intercettata dal raggio $i$ e $f_j$ è il valore dell’attenuazione.


<!-- Pagina PDF 127 -->

### 6.7.2 Gli algoritmi ART

Gli algoritmi iterativi appartenenti alla classe degli ART sono tra i più longevi e più usati nel
campo della tomografia fin dai primi anni 70 e si basano su un metodo di risoluzione di sistemi
di equazione teorizzato dal matematico polacco Kaczmarz nel 1937. Se consideriamo il modello
geometrico visto nel precedente paragrafo, possiamo definire il problema del calcolo delle
proiezioni come un problema diretto, dove qualsiasi sia il numero degli angoli di proiezione che
andremo a prendere avremo altrettante incognite da determinare, ovvero le proiezioni stesse. Il
Nel caso invece in cui dobbiamo ricostruire l’oggetto iniziale a partire dai dati di proiezione,
siamo in presenza di un problema inverso e mal posto in quanto il numero delle incognite, questa
volta appartenenti al piano $(x,y)$ dell’oggetto che vogliamo ricostruire, supera il numero delle
equazioni a disposizione. L’obiettivo di questi algoritmi è dunque quello di cercare una stima
accettabile dell’immagine da ricostruire ottimizzando un numero di dati sicuramente inferiore al
numero ideale per una inversione perfetta del sistema. Un’importante struttura dati utile in tal
senso è la
cosiddetta matrice di inversione $A$ o matrice di sistema, già descritta precedentemente (vedi
paragrafo “Trasformata di Radon”). Questa matrice, nel nostro caso di notevoli dimensioni, ha
coefficienti con valore compreso tra 0 e 1 che ci indica, rispetto ad un determinato voxel, qual è
la frazione del raggio che l’attraversa. Gli algoritmi ART semplificano il problema attribuendo
un valore booleano nel caso in cui il raggio attraversa il centro della cella pur non coprendola
interamente (valore 1) oppure non intercetta il centro della cella pur coprendola parzialmente
(valore 0).

Se consideriamo un’immagine di dimensioni $n_x \times n_y$ e la matrice delle proiezioni (sinogramma)
di dimensione $n_a \times n_p$ dove $n_a$ rappresenta la dimensione del vettore di proiezione mentre $n_p$ indica
il numero di proiezioni, la matrice di sistema avrà $n_a \times n_p$ righe per $n_x \times n_y$ colonne. Ciò significa
che se abbiamo a che fare con un’immagine di 512 per 512 pixel la matrice di sistema arriva ad
avere dimensioni pari a 21870 x 262144. Questo è uno dei motivi per cui, dovendo utilizzare un
ingente mole di dati, gli ART sono piuttosto lenti.

Inoltre anche la tecnica di calcolo della matrice di sistema influenza notevolmente i tempi di
ricostruzione e in letteratura sono presenti diverse tecniche che mirano alla minimizzazione del
tempo impiegato.
Il processo iterativo è dato da:

$$
\hat{f}_j^{\,k+1}
=
\hat{f}_j^{\,k}
+
\frac{
g_i-\displaystyle\sum_{j=1}^{N}\hat{f}_{ji}^{\,k}
}{N}
$$

dove $\hat{f}_j^{\,k+1}$ è il valore del pixel j alla k+1-sima iterazione

### 6.7.3 Esempio di applicazione dell’algoritmo ART

Consideriamo un oggetto da ricostruire di dimensioni 2 x 2 e 6 proiezioni.
Partiamo dal calcolo delle proiezioni. L’oggetto dal quale vogliamo estrarre le proiezioni è:

$$
\begin{bmatrix}
5 & 7 \\
6 & 2
\end{bmatrix}
$$

Il nostro sistema avrà le incognite, ovvero le proiezioni, come un vettore colonna di dimensioni $6
\times 1$ e ciò comporta la definizione di una matrice $A$ di sistema di dimensioni $6 \times 4$. La matrice
relativa all’oggetto $f$ viene poi rappresentata in un vettore colonna di dimensioni $4 \times 1$.
Il prodotto tra la matrice di sistema e il vettore colonna degli elementi dell’oggetto $AX$ rappresenta
proprio il vettore delle proiezioni $g$:

$$
A =
\begin{bmatrix}
1 & 0 & 0 & 1 \\
0 & 1 & 0 & 1 \\
0 & 0 & 1 & 1 \\
1 & 1 & 0 & 0 \\
0 & 1 & 1 & 0
\end{bmatrix}
$$

$$
f =
\begin{bmatrix}
5 \\
6 \\
7 \\
2
\end{bmatrix}
$$

$$
\begin{bmatrix}
1 & 0 & 0 & 1 \\
0 & 1 & 0 & 1 \\
0 & 0 & 1 & 1 \\
1 & 1 & 0 & 0 \\
0 & 1 & 1 & 0
\end{bmatrix}
\begin{bmatrix}
5 \\
6 \\
7 \\
2
\end{bmatrix}
=
\begin{bmatrix}
7 \\
8 \\
9 \\
11 \\
13
\end{bmatrix}
$$

La matrice di sistema ha l’utilità pratica di determinare le coordinate dei pixel i cui valori
corrispondenti di attenuazione saranno sommati lungo una certa direzione per ottenere la
proiezione desiderata. Nel nostro caso i sei valori di proiezione fanno riferimento a 4 angoli di
proiezione, in particolare 12 e 8 le proiezioni a 0°, 7 la proiezione a 45°, 9 e 11 le proiezioni a 90°
e infine 13 la proiezione a 135° con angoli crescenti nel senso orario.


<!-- Pagina PDF 129 -->

<img src="./images/fig_6_27_p129.png" alt="Figura pagina 129" style="width:100%;">

Consideriamo il problema inverso ovvero il caso in cui $X$ rappresenta il vettore delle incognite
con $Y$ noto. Risulta evidente che maggiore è il numero delle proiezioni, ovvero maggiori saranno
le equazioni a disposizione, migliore sarà la stima finale dell’oggetto da ricostruire ricordando
che finché questo numero di equazioni sarà minore delle incognite, condizione che solitamente si
verifica, avremo sempre a che fare con un’approssimazione dell’oggetto reale. La tecnica
utilizzata dagli algoritmi ART consiste in tre fasi:
- Creare una stima iniziale dell’immagine, ovvero una matrice di zeri di dimensione n x n
x y
- Calcolare le proiezioni a partire dalla stima (inizialmente nulle)
- Ridefinire la stima basata sulla differenza pesata tra la proiezione desiderata (reale) e la
proiezione effettiva (calcolata): $p_{i+1}=p_i+g(\text{desiderata}-\text{effettiva})$


Riprendendo l’esempio precedente, consideriamo ora come incognite gli elementi $a$, $b$, $c$ e $d$ e le
relative proiezioni:

$$
\begin{array}{c|cc|c}
 & \text{Colonna 1} & \text{Colonna 2} & \text{Somma righe} \\
\hline
\text{Riga 1} & a & b & 12 \\
\text{Riga 2} & c & d & 8 \\
\hline
\text{Somma colonne} & 13 & 11 &
\end{array}
$$

$$
\begin{aligned}
\text{Diagonale principale:} \qquad & a+d=9,\\
\text{Diagonale secondaria:} \qquad & b+c=7.
\end{aligned}
$$

Definiamo la stima iniziale e le sue proiezioni:

$$
\begin{array}{cc|c}
0 & 0 & 0 \\
0 & 0 & 0 \\
\hline
0 & 0 &
\end{array}
\qquad
\begin{aligned}
0+0 &= 0,\\
0+0 &= 0.
\end{aligned}
$$

La stima, rispetto alle proiezioni orizzontali $(\theta= 0°)$ assumendo $g = 1/2$, sarà:

$$
\begin{bmatrix}
a\\
b\\
c\\
d
\end{bmatrix}
=
\begin{bmatrix}
0+\dfrac{12-0}{2}\\[6pt]
0+\dfrac{12-0}{2}\\[6pt]
0+\dfrac{8-0}{2}\\[6pt]
0+\dfrac{8-0}{2}
\end{bmatrix}
=
\begin{bmatrix}
6\\
6\\
4\\
4
\end{bmatrix}
$$

$$
\begin{array}{cc|c}
6 & 6 & 12\\
4 & 4 & 8\\
\hline
10 & 10 &
\end{array}
\qquad
\begin{aligned}
6+4 &= 10,\\
6+4 &= 10.
\end{aligned}
$$


Rivalutiamo ora la stima così ottenuta, rispetto alle proiezioni di $\theta= 90°$:

$$
\begin{bmatrix}
a\\
b\\
c\\
d
\end{bmatrix}
=
\begin{bmatrix}
6+\dfrac{11-10}{2}\\[6pt]
6+\dfrac{9-10}{2}\\[6pt]
4+\dfrac{11-10}{2}\\[6pt]
4+\dfrac{9-10}{2}
\end{bmatrix}
=
\begin{bmatrix}
6.5\\
5.5\\
4.5\\
3.5
\end{bmatrix}
$$

$$
\begin{array}{cc|c}
6.5 & 5.5 & 12\\
4.5 & 3.5 & 8\\
\hline
11 & 9 &
\end{array}
\qquad
\begin{aligned}
6.5+3.5 &= 10,\\
5.5+4.5 &= 10.
\end{aligned}
$$

Infine, rivalutiamo la matrice rispetto alle proiezioni di $\theta= 45°$:

$$
\begin{bmatrix}
a\\
b\\
c\\
d
\end{bmatrix}
=
\begin{bmatrix}
6.5+\dfrac{7-10}{2}\\[6pt]
4.5+\dfrac{13-10}{2}\\[6pt]
5.5+\dfrac{13-10}{2}\\[6pt]
3.5+\dfrac{7-10}{2}
\end{bmatrix}
=
\begin{bmatrix}
5\\
6\\
7\\
2
\end{bmatrix}
$$

$$
\begin{array}{cc|c}
5 & 7 & 12\\
6 & 2 & 8\\
\hline
11 & 9 &
\end{array}
\qquad
\begin{aligned}
5+2 &= 7,\\
7+6 &= 13.
\end{aligned}
$$

Come possiamo vedere, le proiezioni ottenute coincidono con le proiezioni desiderate e l’oggetto
è stato ricostruito. Tuttavia utilizzando dati reali è possibile osservare che la stima è influenzata
dal rumore dovuto alla misura e la convergenza ad una stima accettabile può essere molto lenta o
in alcuni casi addirittura non garantita. [6]

### 6.7.4 Altro esempio di applicazione dell’algoritmo ART ([2])

<img src="./images/fig_6_34_p131.png" alt="Figura pagina 131" style="width:100%;">

Gli esempi che abbiamo visto presentano un meccanismo di correzione del pixel in questione di
tipo additivo, tuttavia in letteratura sono presenti diverse tipologie di algoritmi ART che possono
differire sia per quanto riguarda il metodo di correzione e sia per quanto riguarda il criterio scelto
per stabilire il numero di iterazioni da effettuare. La correzione può infatti avvenire subito dopo
il calcolo della differenza (errore) tra la proiezione desiderata ed effettiva oppure alla fine di ogni
iterazione, mentre la correzione può anche essere di tipo moltiplicativo come avviene per gli
algoritmi MART (multiplicative algebraic reconstruction techiniques)

### 6.7.5 Metodi ai minimi quadrati

Questa classe di algoritmi, conosciuti anche come least squares methods o più semplicemente LS,
presenta un approccio diverso rispetto agli ART nonostante rimane in comune l’idea di utilizzare
un metodo iterativo che di volta in volta migliora la stima dell’immagine. Anche in questo caso
si tratta di andare a lavorare numericamente sul singolo pixel ma, mentre per quanto riguarda gli
ART il criterio scelto per ottenere un risultato soddisfacente poteva essere la via empirica o il
raggiungimento di una soglia prefissata, tipicamente la differenza tra i valori di due iterazioni
successive relative allo stesso pixel, per quanto riguarda il metodo ai minimi quadrati occorre
utilizzare una particolare funzione, detta funzione obiettivo, che deve essere minimizzata.
Questa funzione particolare dipende essenzialmente dal modello che abbiamo scelto per
descrivere il nostro sistema ed anche in questo caso utilizzeremo il modello già precedentemente
descritto dove le proiezioni sono ottenute come:

$$
p_i
=
\sum_{j=1}^{n} w_{ij}f_j,
\qquad
i=1,2,\ldots,m
$$

Ricordiamo che nella struttura matriciale sia le $p_i$ proiezioni che gli elementi $f_j$ reali dell’immagine
che vogliamo ricostruire sono vettori colonna, mentre $w_{ij}$ rappresenta gli elementi della matrice
di sistema $A$ utile per l’inversione del problema.
Partiamo prima dal caso generale in cui abbiamo due vettori $x$ e $y$ costituiti da $n$ elementi, dove $x$
rappresenta i dati dai quali vogliamo ricavare una stima di $y$ accettabile, ovvero una funzione $f$
tale che $f(x_i) \approx y_i$ . La nostra $f(x_i)$ sarà quindi accettabile quando sarà resa minima la funzione $S$ così
definita:

$$
S
=
\sum_{i=1}^{n}
\left(y_i-f(x_i)\right)^2
$$

Nel nostro caso la $f(x_i)$ sarà data dal termine $w_{ij}f_j$ dove $f_j$ nel caso del problema inverso
rappresenta gli elementi incogniti dell’immagine da ricostruire a partire da una certa stima
iniziale. Per distinguere dal problema diretto d’ora in poi in luogo di $f_j$ utilizzeremo $\hat{f}$ cioè la
stima, ovvero quella struttura dati nel piano $(x,y)$ che dovrà tendere il più possibile ad
un’immagine reale. La funzione da minimizzare sarà invece data da:

$$
S(\hat{f})
=
\frac{1}{2}
\sum_{i=1}^{n}
\left(\hat{y}_i-\hat{f}_i\right)^2
\Sigma^{-1}
$$

dove $\Sigma$ è una matrice contenente le deviazioni standard del valore del pixel.
E’ importante ricordare che questo metodo viene utilizzato anche per la ricostruzione di immagini
tomografiche in medicina nucleare, ovvero PET e SPECT, dove entrano in gioco una serie di
considerazioni riguardanti la distribuzione spaziale dei radioisotopi nel tessuto e successivamente
la stima dell’emissività del tessuto stesso. Solitamente viene introdotta un’ulteriore funzione detta
penalità, infatti questi algoritmi sono citati come PWLS (penalized weighted least squares). Ciò
comporta l’inserimento di dati e parametri aggiuntivi rispetto all’utilizzo di tali algoritmi per le
immagini a raggi X.


Una forma modificata del metodo LS, detta OSWLS (organized subsets weighted least squares),
consiste nel suddividere le proiezioni suddivise in pacchetti di dati chiamati subset, a causa del
loro elevato numero; per ciascuna iterazione vengono eseguite le operazioni per ogni subset. Il
numero dei subset non viene stabilito a priori ma calcolato direttamente dall’algoritmo in base al
numero delle proiezioni considerato e al numero di iterazioni prescelto.

### 6.7.6 Metodo ML-EM (maximum likelihood - Expectation maximization):

Il concetto di base della ricostruzione iterativa basata su metodi di massima verosimiglianza è che
la distribuzione di attività nella fetta ricostruita è quella che ha la massima probabilità di produrre
i dati di proiezione osservati. Poichè non è disponibile nessuna soluzione analitica, la
ricostruzione deve essere effettuata iterativamente, in genere con l’utilizzo di algoritmi di
massimizzazione dei valori attesi.
Una delle principali caratteristiche di questo metodo è che esso permette di includere
nell’algoritmo le proprietà statistiche del fenomeno di annichilazione/emissione/trasmissione dei
fotoni (cosa non possibile negli algoritmi analitici) . Al fine di evidenziare questa caratteristica ,
il metodo ML-EM verrà qui descritto per la ricostruzione di immagini di Medicina Nucleare. Per
dettagli sul modello statistico dell’emissione, vedi Appendice B.

L’algoritmo ML-EM cerca di produrre una immagine che sia statisticamente la più probabile fra
quelle in grado di generare le proiezioni osservate. Questo metodo permette di tener conto
dell’attenuazione, della natura statistica del processo di acquisizione, della perdita di risoluzione
sia durante la proiezione che durante la retroproiezione. Esso calcola la proiezione di errore dal
rapporto dei set di proiezione e genera una correzione moltiplicativa alla stima di immagine.
Vogliamo risolvere l’equazione $g = Af$, dove $g$ è il vettore dei valori nel sinogramma, $A$ è la
matrice data, e $f$ è il vettore incognito dei valori dei pixel nell’ immagine che deve essere
ricostruita. Nel caso di ricostruzione di immagini PET le misurazioni sono soggette a variazioni
a causa del fenomeno probabilistico di Poisson della disintegrazione di radioattività. L’obiettivo
dell’algoritmo ML-EM è di cercare una soluzione generale come migliore stima per $f$: il numero
medio di disintegrazioni di radioattività $f$ nell’immagine che può produrre il sinogramma $g$ con
alta probabilità.
Questo può essere fatto usando la legge di Poisson che permette di predire la probabilità del
numero di conteggi rivelati, dato il numero medio di disintegrazioni. Quindi ogni iterazione
dell’algoritmo è divisa in due passi: nel passo expectation (E step) viene compiuta la formula che
esprime la probabilità di ottenere qualsiasi immagine ricostruita, dati i dati misurati, e nel passo
maximization (M step) viene trovata l’immagine che ha la più alta probabilità. Questo porta
all’algoritmo ML-EM, di Lange e Carson.

$$
\hat{f}_j^{\,k+1}
=
\frac{\hat{f}_j^{\,k}}
{\displaystyle\sum_{i=1}^{n} a_{ij}}
\sum_{i=1}^{n}
\frac{g_i}
{\displaystyle\sum_{j'=1}^{m} a_{ij'}\hat{f}_{j'}^{\,k}}
\,a_{ij}
$$

La prima immagine $F_0$ può per esempio essere ottenuta dall’algoritmo FBP (in questo caso i valori
negativi dovrebbero essere forzati a 0). L’equazione precedente deve essere applicata pixel per
pixel e può essere interpretata come:
ad ogni iterazione $k$, è disponibile una stima corrente dell’immagine. Le proiezioni
misurate sono poi confrontate con le proiezioni simulate della stima corrente, e il
rapporto tra le proiezioni simulate e le proiezioni misurate è usato per modificare la
corrente stima per produrre una stima modificata (possibilmente, più accurata) la quale
diventa l’iterazione $k + 1$.
Questo processo è ripetuto molte volte.

Dettagli su come ottenere la (69) sono descritti in [2].

### 6.7.7 Descrizione Algoritmo ML-EM

La funzione da massimizzare è la seguente:

$$
\log k(f,\lambda)
=
\sum_{i=1}^{I}
\left[
-\hat{f}_i(\lambda)
+
f_i\log \hat{y}_i(\lambda)
\right]
$$

con $\lambda$ esponente di Poisson; trascurando coincidenze random e scatter, la stima delle proiezioni fi
(sinogramma) è:

$$
\hat{f}_i(\lambda)
=
\sum_{j=1}^{P}
a_{ij}\lambda_j
$$

con $a_{ij}$ coefficiente della matrice di sistema e $\lambda_j$ emissione del $j$-esimo pixel.
Secondo il modello Poissoniano (vedi Appendice B) le $fi$ rappresentano le realizzazioni della
variabile casuale $F_i$ distribuita come:

$$
F_i
=
\operatorname{Poisson}\!\left(
\sum_{j=1}^{P} N_{ij}
\right)
=
\operatorname{Poisson}\!\left(
\sum_{j=1}^{P} a_{ij}\lambda_j
\right)
$$

dove $N_{ij}$ indica il numero di emissioni dal $j$-esimo pixel che vengono rivelate dall’$i$-esimo detettore,
la somma è effettuata su tutti i $P$ pixels visti dal singolo detettore contemporaneamente. In generale
può essere difficile massimizzare la $k(f, \lambda)$ rispetto a $\lambda$; una possibile soluzione è eseguire
l’esperimento in uno spazio campione più grande dove i problemi di ottimizzazione sono più facili
da risolvere.

L’algoritmo **ML-EM** richiede l’esistenza di un vettore casuale $(\mathbf{X})$ tale che $(F)$ sia una funzione $(h(\mathbf{X}))$ di $(\mathbf{X})$. Si suppone inoltre che $(\mathbf{X})$ abbia una funzione di densità di probabilità $(g(\mathbf{X},\lambda))$ rispetto a una misura $(\mu_{\mathbf{X}})$.

Sotto queste ipotesi, la funzione $(k(f,\lambda))$ può essere ottenuta per integrazione:

$$
k(f,\lambda)
=
\int g(\mathbf{X},\lambda)\,d\mu(\mathbf{X}),
\qquad
\mathbf{X}:h(\mathbf{X})=F
$$

Ogni iterazione dell’algoritmo **MLEM** è composta da due passi.

Nel **passo E** si costruisce il valore atteso condizionato:

$$
E\left[
\log g(\mathbf{X},\lambda)
\mid
F,\lambda^n
\right]
$$

dove $(\lambda^n)$ indica la stima attuale dei parametri, cioè quella relativa all’$(n)$-esima iterazione.

Nel **passo M**, questo valore atteso viene massimizzato rispetto a $(\lambda)$, mantenendo $(\lambda^n)$ fissato.


L’algoritmo ML-EM converge lentamente e può richiedere moltissime iterazioni. L’algoritmo
(OSEM) (Ordered-subsets expectation maximization) è stato proposto da Hudson e Larkin per
accelerare il processo di ricostruzione usando l’algoritmo ML-EM. Con questo metodo, l’insieme
di proiezioni è diviso in sottoinsiemi. Per esempio, se ci sono 64 proiezioni (acquisite da 64
angoli) queste vengono suddivise in 16 sottoinsiemi. Dopo viene applicato l’algoritmo ML-EM
per ogni sottoinsieme. L’uso di 16 sottoinsiemi dovrebbe accelerare la convergenza
dell’algoritmo. Nell’algoritmo OSEM i dati delle proiezioni angolari, cioè le colonne del
sinogramma, sono raggruppati in sottoinsiemi ordinati di rivelatori (quindi un sottoinsieme
riunisce tutte le proiezioni calcolate ad un certo angolo); il metodo ML-EM viene applicato ad
ogni sottoinsieme aggiornando simultaneamente tutti i pixel che appartengono ad esso, dopodichè
si stimano le misure e si passa al successivo sottoinsieme. All’interno della singola iterazione si
percorrono tutti i sottoinsiemi, cioè si usa tutta l’informazione contenuta nel sinogramma.

# 6.8 Appendice A - Proprietà della trasformata di Radon

La seguente lista mostra alcune delle proprietà della trasformata di Radon. In tutto l'elenco si assume la corrispondenza:

$$
f(x,y) \xleftrightarrow{\mathrm{Radon}} g(s,\theta)
$$

La proiezione può essere indicata anche con $p_\theta(s)$ anziché con $g(s,\theta)$.

## Linearità

Se

$$
f(x,y) \xleftrightarrow{\mathrm{Radon}} p(s,\theta),
\qquad
h(x,y) \xleftrightarrow{\mathrm{Radon}} q(s,\theta),
$$

allora:

$$
\alpha f(x,y)+\beta h(x,y)
\xleftrightarrow{\mathrm{Radon}}
\alpha p(s,\theta)+\beta q(s,\theta).
$$

## Shift / traslazione

$$
f(x-x_0,y-y_0)
\xleftrightarrow{\mathrm{Radon}}
p_\theta\!\left(s-x_0\cos\theta-y_0\sin\theta\right).
$$

## Rotazione

$$
f\!\left(
x\cos\theta' + y\sin\theta',
-x\sin\theta' + y\cos\theta'
\right)
\xleftrightarrow{\mathrm{Radon}}
p_{\theta-\theta'}(s).
$$

## Simmetria circolare

Per una funzione a simmetria circolare:

$$
f_0(s,\theta)=f_0(s,0),
\qquad \forall\,\theta,
$$

quindi:

$$
p_\theta(s)=p_0(s),
\qquad \forall\,\theta.
$$

## Simmetria e periodicità

$$
p_\theta(s)
=
p_{\theta\pm\pi}(-s)
=
p_{\theta\pm k\pi}\!\left((-1)^k s\right),
\qquad \forall\,k\in\mathbb{Z}.
$$

## Scala affine

$$
f(\alpha x,\beta y)
\xleftrightarrow{\mathrm{Radon}}
\frac{1}{
\sqrt{(\beta\cos\theta)^2+(\alpha\sin\theta)^2}
}
p_{\angle_\pi(\beta\cos\theta,\alpha\sin\theta)}
\!\left(
\frac{s\,|\alpha|\,|\beta|}
{\sqrt{(\beta\cos\theta)^2+(\alpha\sin\theta)^2}}
\right).
$$

Le due proprietà seguenti sono casi particolari della proprietà di scala affine.

### Ingrandimento / riduzione

$$
f(\alpha x,\alpha y)
\xleftrightarrow{\mathrm{Radon}}
\frac{1}{|\alpha|}\,p_\theta(\alpha s),
\qquad \alpha\neq 0.
$$

### Ribaltamenti (flip)

$$
f(x,-y)
\xleftrightarrow{\mathrm{Radon}}
p_{\pi-\theta}(-s),
$$

$$
f(-x,y)
\xleftrightarrow{\mathrm{Radon}}
p_{\pi-\theta}(s).
$$

## Conservazione del volume

$$
\int_{-\infty}^{\infty}
\int_{-\infty}^{\infty}
f(x,y)\,dx\,dy
=
\int_{-\infty}^{\infty}
g(s,\theta)\,ds,
\qquad \forall\,\theta.
$$

---

# 6.9 Appendice B - Modello statistico dell'emissione

Il fenomeno dell'emissione può essere descritto considerando un campione di materiale contenente $N$ nuclei radioattivi. Se $p$ è la probabilità che un singolo nucleo decada in un dato intervallo temporale, la probabilità $P(k)$ che nello stesso intervallo decadano $Z=k$ nuclei, dove $Z$ è la variabile casuale che indica il numero di fotoni emessi, è descritta da una distribuzione binomiale:

$$
P(k)
=
\frac{N!}{k!(N-k)!}
p^k(1-p)^{N-k}.
\tag{B.1}
$$

La distribuzione binomiale è asimmetrica e presenta media $\bar{n}$ e varianza $\sigma^2$ pari a:

$$
\bar{n}
=
\sum_{k=0}^{N} kP(k)
=
pN,
$$

$$
\sigma^2
=
\sum_{k=0}^{N}(k-\bar{n})^2P(k)
=
p(1-p)N.
$$

Applicando questo modello al caso della SPECT, si considera un intervallo temporale $\delta t$ molto più piccolo del tempo caratteristico di decadimento $T_e$ del radioisotopo:

$$
\delta t \ll T_e.
$$

La probabilità $p$ che un nucleo decada durante l'intervallo $\delta t$ è quindi molto piccola e può essere espressa come:

$$
p=\lambda\,\delta t.
$$

È possibile passare dal modello binomiale al modello di Poisson imponendo le condizioni limite:

$$
N\to\infty,
\qquad
p\to 0,
\qquad
Np=\lambda.
$$

Si ottiene così il modello maggiormente utilizzato nella SPECT. La probabilità di osservare $k$ emissioni nell'intervallo considerato, quando il numero medio di emissioni è $\lambda$, è:

$$
P(Z=k)
=
\frac{e^{-\lambda}\lambda^k}{k!},
\qquad
k=0,1,2,\ldots
$$

Per la distribuzione di Poisson, media e varianza coincidono:

$$
\mathbb{E}[Z]=\lambda,
\qquad
\operatorname{Var}(Z)=\lambda.
$$

> **Nota editoriale.** Nella trascrizione sono stati regolarizzati alcuni evidenti refusi tipografici presenti nel documento originale: il termine $p^k$ nella distribuzione binomiale, le sommatorie nella varianza, la forma completa della distribuzione di Poisson e la notazione della proprietà di ingrandimento/riduzione.

# Materiale aggiuntivo: Ricostruzione iterativa di immagini tomografiche

I seguenti appunti approfondiscono la ricostruzione tomografica come problema lineare inverso, i criteri statistici di stima, gli algoritmi iterativi e i metodi ML-EM, OS-EM e MAP.

![Pagine degli appunti originali - pagina 1](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p01.jpg)

![Pagine degli appunti originali - pagina 2](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p02.jpg)

![Pagine degli appunti originali - pagina 3](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p03.jpg)

![Pagine degli appunti originali - pagina 4](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p04.jpg)

![Pagine degli appunti originali - pagina 5](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p05.jpg)

![Pagine degli appunti originali - pagina 6](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p06.jpg)

![Pagine degli appunti originali - pagina 7](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p07.jpg)

![Pagine degli appunti originali - pagina 8](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p08.jpg)

![Pagine degli appunti originali - pagina 9](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p09.jpg)

![Pagine degli appunti originali - pagina 10](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p10.jpg)

![Pagine degli appunti originali - pagina 11](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p11.jpg)

![Pagine degli appunti originali - pagina 12](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p12.jpg)

![Pagine degli appunti originali - pagina 13](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p13.jpg)

![Pagine degli appunti originali - pagina 14](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p14.jpg)

![Pagine degli appunti originali - pagina 15](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p15.jpg)

![Pagine degli appunti originali - pagina 16](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p16.jpg)

![Pagine degli appunti originali - pagina 17](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p17.jpg)

![Pagine degli appunti originali - pagina 18](./images/ricostruzione_iterativa_appunti/ricostruzione_iterativa_p18.jpg)

