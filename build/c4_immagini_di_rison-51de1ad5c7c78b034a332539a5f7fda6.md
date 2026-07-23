# Capitolo 4: Immagini Di Risonanza Magnetica

<!-- Estratto da: Appunti - Principi fisici ImmaginiBiomediche.pdf, pagine 63-89 -->

<!-- Pagina PDF 63 -->

## 4.0 Materiale utile

Durante il corso verrà utilizzato del materiale didattico disponibile alle seguente pagine web: 

- https://www.mriquestions.com/
- https://www.cis.rit.edu/htbooks/mri/inside.htm


## 4.1 Principi fisici

### 4.1.1 Il nucleo

La proprietà che permette ad un nucleo di interagire con un campo magnetico esterno è il così detto spin
intrinseco. E’ un fenomeno quantistico per il quale il nucleo ruota intorno al proprio asse. I valori assunti
dallo spin, $I$, dipendono dal numero di protoni e neutroni presenti nel nucleo.
Se $I= 0$, non c’è interazione tra il nucleo e il campo magnetico esterno. Noi consideriamo, in questo studio,
solo gli atomi di Idrogeno $^{1}H$ che consistono in un singolo protone che ha spin $I=1/2$.

Il momento angolare, $p$, del nucleo dovuto allo spin $I$ è dato da:

$$
p = \hbar I
$$

dove $\hbar$ è la costante di Planck e $p$ e $I$ sono quantità vettoriali.
dove
Siccome il nucleo ha una carica elettrica e un momento angolare allora ha associato anche un momento
magnetico:

$$
\mu= \gamma p
$$

dove $\gamma$ è il rapporto giromagnetico, costante caratteristica del tipo di nucleo. Per i protoni dell’idrogeno,    

$$
\gamma = 26.75 \times 10^{7}\ \mathrm{rad\,s^{-1}\,T^{-1}}
$$

$$
(\frac{\gamma}{2\pi} = 42.58\,\mathrm{MHz\,T^{-1}})
$$.

### 4.1.2 Interazione con un campo magnetico esterno

Modello quantistico
Possiamo pensare il nucleo dell’idrogeno $^{1}H$ come una barretta magnetica con un polo nord e un polo sud.
Secondo le leggi di meccanica quantistica il momento di dipolo del nucleo può assumere $2I+1$ orientamenti
in un campo magnetico esterno, corrispondenti a $2I+1$ livelli energetici permessi. La “barretta magnetica”,
protone, può quindi allinearsi al campo esterno in posizione parallela o antiparallela. Queste due
orientazioni corrispondono a due livelli energetici la cui differenza, $\Delta E$, è proporzionale all’ampiezza del
campo magnetico esterno $B_0$:

$$
\Delta E = \mu B_0/ I 
$$

o anche

$$
\Delta E = \gamma \hbar B_0 
$$

<img src="./images/fig_4_01_p64.png" alt="Figura pagina 64" style="width:100%;">

*Figura 4.1. Livelli di energia degli spin in un campo magnetico. (sinistra) Livello basso di energia. (destra) Livello alto di energia.*

La transizione tra i due stati può essere indotta dall’applicazione di una radiazione magnetica della corretta
pulsazione. Tale pulsazione è detta frequenza di Larmor ed è data da:

$$
\omega _L = \Delta E /\hbar = \gamma B_0
$$

Questo fenomeno è noto con il nome di risonanza, ossia: solo la radiazione elettromagnetica della corretta
frequenza può far passare il nucleo da una orientazione all’altra.

<img src="./images/fig_4_02_p64.png" alt="Figura pagina 64" style="width:100%;">

*Figura 4.2. Diagramma dei livelli energetici per I=1/2.*

Sebbene il livello di energia più basso è naturalmente preferito, l’energia termica induce transizioni tra un
livello energetico e l’altro cosicché all’equilibrio c’è solo un piccolo eccesso di spin nello stato di energia
più basso. Le due popolazioni all’equilibrio sono date dalla distribuzione di Boltzmann. Se $N_L$ e $N_U$ sono
le popolazioni dei livelli di energia rispettivamente più basso e più alto:

$$
\frac{N_L}{N_U}
=
\exp\left(\frac{\hbar \omega_L}{kT}\right)
\approx
1+\frac{\hbar \omega_L}{kT}
$$

dove $k$ è la costante di Boltzmann e $T$ è la temperatura. L’eccesso di spin nello stato di energia più basso
è:

$$
\frac{N_L-N_U}{N_U}
\approx
\frac{\hbar\omega_L}{kT}
=
\frac{\hbar\gamma B_0}{kT}
$$

<!-- Pagina PDF 65 -->

Questi sono gli spin che possiamo osservare in un esperimento di risonanza magnetica (RM). Per i protoni
alla temperatura ambiente, con campo magnetico $B_0 = 0.1 T$, l’eccesso è solo $7 \times 10^{-7}$. Per incrementare la
sensibilità si può diminuire la temperatura, cosa impraticabile con i pazienti, o aumentare l’intensità del
campo magnetico $B_0$.

#### Modello classico
In effetti il modello quantistico è il modello che dovrebbe essere usato per spiegare tutti i fenomeni di
risonanza magnetica (RM).
Comunque l’uso del modello classico, in cui gli spin possono assumere tutte le orientazioni in un campo
magnetico esterno, risulta migliore dal punto di vista intuitivo per la visualizzazione della maggior parte
degli esperimenti.
Per $I = 1/2$, tutte le previsioni del modello classico si accordano esattamente con la teoria quantistica applicata
ad un sistema macroscopico.
Nel modello classico, l’interazione tra un momento magnetico $\mu$ e un campo magnetico $B_0$ tende ad
allineare i due. Quindi il momento magnetico risente di una forza torcente $L$, data da:

$$
L = \mu \times B_0
$$

Il risultato di tale forza è che il nucleo inizia a precedere intorno a $B_0$ variando il momento angolare $p$:

$$
dp / dt = L = μ \times B_0
$$

Ma essendo: $p = \mu / \gamma $ allora: 

$$
d \mu / dt = \mu \times \gamma B_0 
$$

oppure:

$$
d \mu / dt = \omega _L \times \mu 
$$

dove $\omega = - \gamma B_0$.

Le equazioni (12) e (13) mostrano che i nuclei precedono intorno alla direzione del campo applicato alla
frequenza $\omega _L$.

Il segno meno indica la direzione della rotazione. Notare che la frequenza della rotazione uguaglia la
pulsazione di risonanza dell’equazione (7), (frequenza di Larmor).

#### Magnetizzazione totale
Nella pratica, non si osserva mai un singolo nucleo o il singolo momento magnetico, ma l’effetto
combinato di tutti i nuclei del campione.
Quello che si osserva, perciò, è la magnetizzazione totale $M$, data da:

$$
M = \sum \mu 
$$

Sebbene tutti i nuclei precedano alla velocità $\omega _L $intorno a $B_0$, all’equilibrio i momenti magnetici dei nuclei
non hanno una direzione preferenziale sul piano perpendicolare al campo applicato. In altre parole, non
esiste coerenza di fase tra i diversi $\mu$ che costituiscono la magnetizzazione totale, tanto che, all’equilibrio,
$M$ non ha componente perpendicolare a $B_0$.
C’è invece una componente lungo $B_0$, dovuta al fatto che i momenti magnetici tendono ad allinearsi al
campo magnetico esterno. L’ampiezza di $M$ all’equilibrio è uguale a quella predetta dal modello quantistico
nell’equazione (8).

$M$ si comporta come un momento magnetico che, se perturbato dal suo stato di equilibrio, precede alla
frequenza $\omega _L$ intorno a $B_0$.
Allora in analogia con l’equazione (13), possiamo scrivere:

$$
dM/dt = \omega _L \times M = \gamma M \times B_0
$$

### 4.1.3 Impulsi a radio frequenza (RF)
Nell’esperimento di risonanza magnetica (RM) si rivela la magnetizzazione totale e per fare questo è
necessario perturbare in qualche modo il sistema che si trova nel suo stato di equilibrio e costringere $M$ ad
allontanarsi dalla direzione parallela a $B_0$.
L’impulso di eccitazione è dato dall’applicazione di un secondo campo magnetico $B_1$, perpendicolare a $B_0$
e rotante attorno a $B_0$ alla velocità $\omega _L$ in sincronismo con la precessione dei momenti magnetici nucleari.

Visto dal sistema di riferimento del laboratorio, il campo $B_1$ causa lo spostamento di $M$ dalla posizione di
riposo parallela a $B_0$ e lo costringe ad eseguire una traiettoria a spirale (*Figura 4.3*).

<img src="./images/fig_4_03_p66.png" alt="Figura pagina 66" style="width:100%;">

*Figura 4.3. Vettore di magnetizzazione nel sistema di riferimento fisso.*

Quando viene spento $B_1$, $M$ continua a precedere descrivendo un cono ad un angolo $\alpha$ da $B_0$.
La grandezza di questo angolo, (flip angle), dipende dall’ampiezza di $B_1$ e dal tempo della sua applicazione.

Infatti:

$$
\alpha = \gamma B_1 t_p
$$

dove $t_p$ è la durata dell’impulso $B_1$.

<!-- Pagina PDF 67 -->

<img src="./images/fig_4_04_p67.png" alt="Figura pagina 67" style="width:100%;">

*Figura 4.4. $M$ descrive un cono di un angolo $\alpha$ di flip.*

Se $B_1$ è applicato per un tempo opportuno, si può causare il posizionamento di $M$ a 90° rispetto a $B_0$. In
questo caso l’applicazione di $B_1$ è chiamata "impulso a 90 gradi". Si può causare anche il posizionamento
di $M$ in direzione $-B_0$. Questo è un "impulso a 180 gradi" o "impulso di inversione".

$B_1$ è anche detto "campo magnetico a radiofrequenza" perché $\omega _L/2 \pi$ è normalmente compreso tra 1 MHz
e 500 MHz, frequenze che corrispondono alle onde radio. Quindi gli impulsi $B_1$ sono chiamati anche
"impulsi a radiofrequenza".

Il secondo campo magnetico $B_1$ che provoca l’eccitazione dei nuclei del campione, è generato
dall’applicazione di una tensione elettrica oscillante ai terminali di una bobina solenoidale il cui asse è
perpendicolare alla direzione di $B_0$. La bobina è accordata alla frequenza di risonanza dalla presenza di un
capacitore posto in parallelo. La tensione imposta oscilla alla frequenza di risonanza $\omega _L$ e quindi la corrente
oscillante che scorre nella bobina genera un campo magnetico anch’esso oscillante ($B_1$), perpendicolare a
$B_0$ (*Figura 4.5*).

<img src="./images/fig_4_05_p67.png" alt="Figura pagina 67" style="width:100%;">

*Figura 4.5. Schema di bobina RF per la generazione del campo magnetico B1.*


<!-- Pagina PDF 68 -->

### 4.1.4 Segnale di decadimento libero (FID)

Dopo l’applicazione dell’impulso a 90°, il vettore di magnetizzazione $M$ genera esso stesso un campo
magnetico oscillante. Questo può essere rivelato perché capace di indurre una corrente alternata nella
bobina, la stessa bobina che è usata per applicare il campo $B_1$ come visto nel paragrafo precedente. Tale
bobina (lo schema è mostrato in *Figura 4.6*) è detta "a radiofrequenza".

<img src="./images/fig_4_06_p68.png" alt="Figura pagina 68" style="width:100%;">

*Figura 4.6. La precessione della magnetizzazione induce una corrente oscillante nella bobina che viene rivelata dal ricevitore.*

Il segnale indotto dal vettore di magnetizzazione aumenta durante l’impulso a 90° e dopo tale impulso
decade a zero a causa del rilassamento che fa tornare $M$ alla sua posizione di equilibrio, $M_0$, parallela a $B_0$.
Questo tipo di segnale di decadimento, ottenuto in assenza di $B_1$, è chiamato segnale di decadimento libero
ed in inglese è detto FID (Free Indunction Decay) oppure FIS (Free Indunction Signal), *Figura 4.7*.

<img src="./images/fig_4_07_p68.png" alt="Figura pagina 68" style="width:100%;">

*figura 4.7. Segnale di decadimento libero successivo all’impulso di 90 gradi.*

### 4.1.5 Il sistema di riferimento rotante
Noi siamo interessati al comportamento del vettore di magnetizzazione durante le sequenze di
impulsi.
Il movimento del vettore $M$ visto dal laboratorio risulta molto complicato e difficile da visualizzare,
specialmente quando sono applicati due o più impulsi. Invece di considerare il movimento della
magnetizzazione nel sistema di riferimento fisso, possiamo farlo dal punto di vista di un osservatore che
ruota attorno all’asse parallelo a $B_0$, in sincronismo con i momenti magnetici nucleari. Questo è il cosiddetto
sistema di riferimento rotante.

#### Equazioni di moto nel sistema di riferimento rotante
Vogliamo riscrivere l’equazione (15) nel sistema di riferimento rotante. Il vettore $M$ può essere
decomposto in tre componenti, una per ogni asse del sistema di riferimento relativo:

$$
\mathbf{M} = M_{x'} \mathbf{i} + M_{y'} \mathbf{j} + M_{z'} \mathbf{k}
$$

con $\mathbf{i}$, $\mathbf{j}$, $\mathbf{k}$  versori degli assi $x'$, $y'$, $z'$ del sistema di riferimento relativo.

La derivata nel tempo di $M$ è:

$$
\frac{d\mathbf{M}}{dt}
=
\frac{dM_x}{dt}\,\mathbf{i}
+
M_x\frac{d\mathbf{i}}{dt}
+
\frac{dM_y}{dt}\,\mathbf{j}
+
M_y\frac{d\mathbf{j}}{dt}
+
\frac{dM_z}{dt}\,\mathbf{k}
+
M_z\frac{d\mathbf{k}}{dt}
$$

$$
=
\left(
\frac{dM_x}{dt}\,\mathbf{i}
+
\frac{dM_y}{dt}\,\mathbf{j}
+
\frac{dM_z}{dt}\,\mathbf{k}
\right)
+
\left(
M_x\frac{d\mathbf{i}}{dt}
+
M_y\frac{d\mathbf{j}}{dt}
+
M_z\frac{d\mathbf{k}}{dt}
\right)
$$

dove $\mathbf{i}$, $\mathbf{j}$, $\mathbf{k}$ sono vettori unitari che cambiano direzione e non modulo.

La rotazione del sistema di riferimento relativo rispetto al sistema fisso è descritto da:

$$
\frac{d\mathbf{i}}{dt}
=
\bar{\boldsymbol{\omega}}\times\mathbf{i},
\qquad
\frac{d\mathbf{j}}{dt}
=
\bar{\boldsymbol{\omega}}\times\mathbf{j},
\qquad
\frac{d\mathbf{k}}{dt}
=
\bar{\boldsymbol{\omega}}\times\mathbf{k}
$$

dove il moto rotatorio avviene attorno ad un asse parallelo a $\bar{\boldsymbol{\omega}}$ ad una velocità di $\omega$ radianti al secondo.

$$
\left(\frac{d\mathbf{M}}{dt}\right)_{\mathrm{lab}}
=
\left(\frac{d\mathbf{M}}{dt}\right)_{\mathrm{rot}}
+
\bar{\boldsymbol{\omega}}\times\mathbf{i}\,M_{x'}
+
\bar{\boldsymbol{\omega}}\times\mathbf{j}\,M_{y'}
+
\bar{\boldsymbol{\omega}}\times\mathbf{k}\,M_{z'}
$$

$$
=
\left(\frac{d\mathbf{M}}{dt}\right)_{\mathrm{rot}}
+
\bar{\boldsymbol{\omega}}\times\mathbf{M}
$$

Abbiamo inoltre visto dalla (15) che :

$$
\left(\frac{d\mathbf{M}}{dt}\right)_{\mathrm{lab}}
=
\gamma\,\mathbf{M}\times\mathbf{B}_0
$$

Allora l’equazione (23) diventa :

$$
\gamma\,\mathbf{M}\times\mathbf{B}_0
=
\left(\frac{d\mathbf{M}}{dt}\right)_{\mathrm{rot}}
+
\bar{\boldsymbol{\omega}}\times\mathbf{M}
$$

così:

$$
\left(\frac{d\mathbf{M}}{dt}\right)_{\mathrm{rot}}
=
\gamma\,\mathbf{M}\times
\left(
\mathbf{B}_0+\frac{\bar{\boldsymbol{\omega}}}{\gamma}
\right)
$$

oppure:

$$
\left(\frac{d\mathbf{M}}{dt}\right)_{\mathrm{rot}}
=
\gamma\,\mathbf{M}\times\mathbf{B}_{\mathrm{eff}}
$$

dove

$$
\mathbf{B}_{\mathrm{eff}}
=
\mathbf{B}_0
+
\frac{\bar{\boldsymbol{\omega}}}{\gamma}
$$

La magnetizzazione precede intorno a $\mathbf{B}_{\mathrm{eff}}$, il campo magnetico effettivo nel sistema di riferimento rotante.
Il termine $\frac{\bar{\boldsymbol{\omega}}}{\gamma}$ è un campo magnetico fittizio che deriva dalla rotazione del sistema di riferimento relativo.
La velocità di rotazione, $\omega$, è la stessa del campo magnetico $\mathbf{B}_{\mathrm{1}}$ a radiofrequenza. Se inoltre siamo
precisamente nella condizione di risonanza:

$\omega = \omega _L$

e

$$
\mathbf{B}_{\mathrm{eff}}
=
\mathbf{B}_0
+
\frac{\bar{\boldsymbol{\omega}}_L}{\gamma}
=
\mathbf{B}_0
+
\frac{-\gamma \mathbf{B}_0}{\gamma}
=
0
$$

Quindi essendo $\mathbf{B}_{\mathrm{eff}} = 0$ non c’è precessione del vettore di magnetizzazione nel sistema di riferimento rotante.

### 4.1.6 Parametri di interazione tessuto-RM

Il contrasto nelle immagini di risonanza magnetica dipende dalle diverse proprietà magnetiche dei tessuti.
Sebbene ci siano molti parametri che influenzano il segnale proveniente dal campione sotto osservazione,
i parametri comunemente usati sono: la densità protonica, $T_1$ e $T_2$. Questi parametri possono avere valori
diversi per tessuti diversi e anche valori diversi per uno stesso tessuto che si trovi in uno stato normale o
patologico.

#### Densità protonica
La maggior parte degli atomi di Idrogeno nel corpo umano costituiscono le molecole di acqua e sono proprio
queste molecole che andiamo a rivelare con l’esperimento di Risonanza Magnetica.
Il termine densità protonica si riferisce semplicemente al numero di protoni per unità di volume ed è
effettivamente proporzionale alla densità di acqua nei tessuti. Quindi ad esempio l’osso ha una densità
d’acqua molto bassa, il fegato alta ed il sangue molto alta.
La densità protonica del tessuto osservato è semplicemente proporzionale alla ampiezza iniziale del segnale
di decadimento libero o FIS immediatamente dopo la fine dell’impulso di eccitazione a 90°. Questo è
abbastanza ovvio intuitivamente, infatti se immaginiamo di osservare oggetti della stessa grandezza ma con
un numero di atomi di idrogeno diverso, si ottiene che l’ampiezza del vettore di magnetizzazione totale di
ciascuno oggetto (dato dalla somma dei momenti magnetici degli atomi di idrogeno contenuti in esso) è
proporzionale alla sua densità protonica. Quindi il segnale che ne risulta, essendo proporzionale
all’ampiezza del vettore di magnetizzazione, è proporzionale alla densità protonica dell’oggetto. Al limite
un campione che non contiene protoni dà un segnale nullo.
Si può, in definitiva identificare la densità protonica con $M_0$, magnetizzazione di equilibrio.

<!-- Pagina PDF 71 -->

#### Rilassamento
Il rilassamento degli spin è causato dallo scambio di energia tra uno spin e l’altro e tra lo spin e l’ambiente
che lo circonda. Queste interazioni danno origine a due tipi di decadimento del vettore $M$, chiamati
rilassamento "spin-spin" e rilassamento "spin-reticolo", rispettivamente. Il risultato finale del rilassamento
è il ritorno di $M$ nel suo stato iniziale parallelo a $B_0$.

Il rilassamento spin-spin è causato dall’interazione dei momenti magnetici nucleari.
Il campo magnetico che ciascun nucleo esperimenta istantaneamente è certamente dominato dal campo
esterno applicato $B_0$, ma c’è anche un contributo al campo locale proveniente dai nuclei più vicini. Queste
interazioni dipolo-dipolo provocano una debole variazione della velocità di precessione di ciascun nucleo.
Il risultato di ciò è una perdita della coerenza della fase dei nuclei tra loro, cosicché la componente
trasversale del vettore di magnetizzazione $M$, cioè la componente perpendicolare al campo $B_0$, è ridotta a
zero (*Figura 4.8*). La costante di tempo del decadimento trasversale $M_{xy}$ è data da $T_2$.

<img src="./images/fig_4_08_p71.png" alt="Figura pagina 71" style="width:100%;">

*Figura 4.8. Il rilassamento Spin-Spin.*

Il rilassamento spin-reticolo causa il graduale riallineamento dei momenti magnetici con $B_0$. Quindi la
componente di $M$ parallela a $B_0$, ossia la componente longitudinale, torna al valore di equilibrio $M_0$ (*Figura 4.9*) in un tempo caratteristico $T_1$.
Una volta che il vettore di magnetizzazione $M$ è tornato al suo valore di equilibrio $M_0$ parallelo a $B_0$, non
c’è nessuna possibilità di avere una magnetizzazione traversa diversa da zero. Per questo motivo $T_2$ è
sempre minore o al limite uguale a $T_1$.

<!-- Pagina PDF 72 -->

<img src="./images/fig_4_09_p72.png" alt="Figura pagina 72" style="width:100%;">

*Figura 4.9. Il rilassamento Spin-Reticolo causa il ritorno della componente.*

#### Pseudo-rilassamento
La presenza di una disomogeneità del campo magnetico all’interno del campione causa
inevitabilmente un ulteriore defasamento relativo dei nuclei tra loro, tanto che è necessario
definire un altro tempo di rilassamento, $T_2^*$, esprimendo la velocità di decadimento trasversale
osservata, $1/T_2^*$, come la somma di due contributi:

- il contributo del rilassamento spin-spin
- il contributo del rilassamento dato dalla disomogeneità di campo magnetico

E quindi:

$$
1/T_2^* = 1/T_2 + 1/T_2^{disom}
$$

Dove: 

$$
1/T_2^{disom} = \gamma \Delta B_0
$$

in cui $\Delta B_0$ è l’ampiezza della variazione di campo magnetico applicato, nella regione occupata
dal campione.

In tabella 4.1 sono riportati i valori caratteristici di $T_1$, $T_2$ e densità protonica di tessuti della testa (con
campo $B_0 = 1.5T$ ).

| Tessuto | $T_1$ (ms) | $T_2$ (ms) | Densità protonica |
|---|---:|---:|---:|
| Grasso | 260 | 85 | 0.8 |
| Materia bianca | 790 | 90 | 0.9 |
| Materia grigia | 520 | 95 | 1.0 |
| Fegato | 490 | 45 |  |
| Rene | 650 | 60 |  |
| Milza | 780 | 60 |  |

*Tabella 4.1*

### 4.1.7 Equazioni di Bloch
I due processi di rilassamento con le due costanti di tempo di decadimento, $T_1$ e $T_2$, possono essere
incorporati all’interno delle famose equazioni di Bloch (Bloch, 1946), che sono ugualmente valide sia nel
sistema di riferimento statico (laboratorio) che in quello rotante:

$$
\frac{dM_x}{dt}
=
\gamma\left(M_yB_z-M_zB_y\right)
-
\frac{M_x}{T_2}
$$

$$
\frac{dM_y}{dt}
=
\gamma\left(M_zB_x-M_xB_z\right)
-
\frac{M_y}{T_2}
$$

$$
\frac{dM_z}{dt}
=
\gamma\left(M_xB_y-M_yB_x\right)
-
\frac{M_z-M_0}{T_1}
$$


### 4.1.8 Sequenze di impulsi
L’ insieme di impulsi a radiofrequenza applicati in un esperimento di risonanza magnetica
nucleare è detto "sequenza di impulsi".

#### Inversion Recovery
La sequenza Inversion Recovery o (IR) consiste in un impulso a 180° seguito, dopo un tempo $T_I$ (detto
Tempo di Inversione), da un impulso a 90° (*Figura 4.10*). Questo tipo di sequenza è usata sia in
spettrometria, per misurare il tempo di rilassamento spin-reticolo di piccoli campioni, sia nelle immagini di
risonanza magnetica, per creare contrasti tra pixel di intensità dipendente dal valore di $T_1$.
In quest’ultimo caso devono essere applicate varie coppie di impulsi di 180° e 90° e tipicamente per
un’immagine di $128 \times 128$ pixel si usano 128 coppie di impulsi IR.

<img src="./images/fig_4_10_p73.png" alt="Figura pagina 73" style="width:100%;">

*Figura 4.10. Sequenza Inversion-Recovery.*

Il valore della componente longitudinale della magnetizzazione dopo un tempo $t$ dall’impulso a 180° può
essere espressa dalla seguente equazione:

$$
M_z(t)
=
M_0\left(1-2e^{-t/T_1}\right)
$$

Dove $M_0$ è la magnetizzazione di equilibrio (equivalente alla densità protonica) e $T_1$ è il tempo di
rilassamento spin-reticolo del campione.

L’intensità del segnale, $S$, immediatamente prima dell’impulso a 90°, in un esperimento di Inversion -
Recovery è proporzionale alla ampiezza di $M_z$ al tempo $TI$, così:

$$
S \propto M_z(\mathrm{TI})
=
M_0\left(1-2e^{-\mathrm{TI}/T_1}\right)
$$

Il grafico in *Figura 4.11* mostra l’andamento di $M_z$ in funzione del tempo, dopo un impulso a 180°. In figura
è evidente la dipendenza di $M_z$ dal valore di $T_1$.

<img src="./images/fig_4_11_p74.png" alt="Figura pagina 74" style="width:100%;">

*Figura 4.11. $M_z$ in funzione del tempo in una sequenza IR.*

L’istante di tempo $t = 0$ corrisponde alla fine dell’impulso a 180, mentre $t = TI$ è l’istante in cui si applica
l’impulso a 90° che converte la $M_z$ in magnetizzazione traversa generando il segnale RM, proporzionale a
$M_z(TI)$. Le tre curve di *Figura 4.11* si riferiscono a tre campioni con valori di $T_1$ crescenti:
la curva più bassa corrisponde al campione con il $T_1$ più lungo, infatti il vettore di magnetizzazione al
tempo $TI$ è ancora negativo, il l’ampiezza iniziale del segnale RM risultante è quindi negativo;
la curva a tratto continuo si riferisce al campione con un valore di $T_1$ intermedio, ampiezza del segnale
positiva;
l’ultima curva, la più alta è quella relativa al valore di T1 più corto, naturalmente l’ampiezza del segnale
risultante è positiva.

#### Sequenza Spin-Echo
La sequenza base consiste in un impulso a 90° seguito da uno a 180°. Il tempo tra i due impulsi è $TE/2$,
dove $TE$ è il Tempo di Eco ($TE$, come sarà descritto in dettaglio più avanti), vedi *Figura 4.12*.

<img src="./images/fig_4_12_p75.png" alt="Figura pagina 75" style="width:100%;">

*Figura 4.12: Sequenza Spin-echo.*

La sequenza spin-echo corregge le disomogeneità di campo magnetico, lasciando solo il segnale di
decadimento dovuto al rilassamento spin-spin.
Fa questo tramite l’impulso a 180° che viene chiamato impulso rifocalizzante. L’ampiezza dell’eco al
tempo $TE$ è data da:

$$
S_2 = S_1 e^{-\mathrm{TE}/T_2}
$$

Riferendoci alla *Figura 4.13* descriviamo in dettaglio la sequenza spin-echo.
Si applica un impulso a 90° (con $B_1$ lungo l’asse $x'$) a seguito del quale la punta del vettore di
magnetizzazione $M$ si sposta dalla sua posizione di equilibrio fino a finire sull’asse $y'$. A causa delle
inevitabili variazioni, all’interno del campione, dell’ampiezza del campo magnetico applicato, i momenti
magnetici nucleari che compongono $M$ cominciano a perdere l’accordo di fase tra loro (vedi *Figura 4.13b*).
Per esempio, se parte del campione risiede in una regione in cui il campo magnetico è più debole rispetto a
$B_0$, i nuclei di questa regione precederanno ad una velocità più bassa di $\omega _0 = \gamma B_0$ nel sistema di riferimento del laboratorio (assi rotanti). Visto dal sistema di riferimento rotante, il vettore di magnetizzazione di questa parte del campione precederà in senso antiorario (perché il sistema relativo ruota precisamente a velocità
$\omega _0$ in senso orario). Al contrario, i vettori di magnetizzazione relativi a zone del campione in cui il campo
magnetico locale è più alto di $B_0$ precederanno, nel sistema di riferimento rotante, in senso orario.

Il risultato totale di tutto questo è che la componente trasversale di $M$ ($M_{xy}$) si riduce esponenzialmente nel
tempo ed il segnale RM che ne risulta è proporzionale a $\exp (-t/T_2^*)$.

- Si applica un impulso di 180° dopo un tempo $TE/2$ dal primo impulso di 90°. La conseguenza è che
tutti i momenti magnetici ruotano intorno all’asse $x'$ (*Figura 4.13c*). Alla fine dell’impulso a 180°, il
ventaglio dei momenti magnetici, che prima si apriva allontanandosi dall’asse $y'$, ora è ribaltato
sull’asse $-y'$.

I vettori di magnetizzazione che precedono più velocemente (dalle parti del campione a più alto campo
magnetico) precedono ancora in senso orario nel sistema di riferimento relativo, ma ora si muovono verso
l’asse $-y'$. Al contrario i vettori delle zone a più basso campo magnetico precedono in senso antiorario nel
sistema relativo ed anch’essi verso l’asse $-y'$ (*Figura 4.13d*).
Al tempo $TE$ dopo il primo impulso tutti sono allineati sull’asse $-y'$, cioè sono stati rifocalizzati
dall’impulso a 180°. Poichè $M$ è la sommatoria di tali momenti magnetici nucleari allora la componente
trasversale $M_{xy}$ raggiunge la sua ampiezza massima a tale istante di tempo (*Figura 4.13e*).


I momenti magnetici si defasano ancora una volta provocando una rapida diminuzione del segnale di
risonanza magnetica (*Figura 4.13f*).

<img src="./images/fig_4_13_p76.png" alt="Figura pagina 76" style="width:100%;">

*Figura 4.13. Esperimento spin-echo visto dal sistema di riferimento rotante.*

#### Sequenza Gradient-echo
I problemi connessi alla misura del segnale di decadimento della magnetizzazione traversa (segnale RM)
immediatamente dopo l’eccitazione dell’impulso a 90° in un esperimento possono essere risolti con la
sequenza Gradient-echo. Questa infatti si serve di un gradiente inverso di lettura che rifasa tra loro gli spin
generando un segnale di eco. (Per una definizione e spiegazione particolareggiata del gradiente, vedi
paragrafo “gradienti di campo magnetico”)
La sequenza Gradient-echo è mostrata in Figura 4.14:

<img src="./images/fig_4_14_p76.png" alt="Figura pagina 76" style="width:100%;">

*Figura 4.14. Sequenza Gradient-echo.*

Viene applicato un impulso a 90° al campione immerso nel campo magnetico esterno $B_0$. Gli spin, a causa
di tale impulso, sono in fase tra loro e la magnetizzazione, e quindi il segnale di risonanza magnetica, è
massimo (*Figura 4.15a*).

<img src="./images/fig_4_15_p77.png" alt="Figura pagina 77" style="width:100%;">

*Figura 4.15. Comportamento dei protoni durante la sequenza Gradient-echo.*

Immediatamente dopo l’impulso a 90° è applicato un gradiente di campo magnetico negativo.
Il gradiente di campo magnetico sarà descritto più in dettaglio in un prossimo paragrafo; esso è un campo
magnetico nella stessa direzione di $B_0$, ma con ampiezza che varia linearmente con la posizione lungo un
asse scelto, per esempio $x$. Grazie alla presenza del gradiente, il campo magnetico a cui è soggetto uno spin
in una posizione generica lungo $x$, ha ampiezza: $B_z(x) = B_0 + x G_x$ dove $G_x$ è il valore di ampiezza del
gradiente aggiunto.

- Gli spin allora inziano a precedere con velocità dipendente dalla posizione occupata da ognuno e
quindi si defasano l’un l’altro in modo “ordinato”, come mostrato la *Figura 4.15b*.
- La successiva applicazione di un gradiente di campo magnetico, questa volta positivo, lungo $x$ (*Figura
4.15c*) provoca un cambiamento del senso di rotazione degli spin e un loro rifasamento che dà origine
all’eco detto “gradient-echo“ (*Figura 4.15d*). Tale eco ha la stessa ampiezza della magnetizzazione
traversa immediatamente dopo l’impulso a 90°.
- Negli istanti successivi al tempo di eco gli spin tornano a sfasarsi tra loro e la magnetizzazione decade
(*Figura 4.15e*).

## 4.2 Principi fisici della formazione di immagini RM
### 4.2.1 Gradiente di campo magnetico

Una parte essenziale del sistema per la generazione di immagini di RM è il gradiente di campo magnetico
che permette di ottenere informazioni spaziali dall’analisi del segnale RM. Un gradiente di campo è un
campo aggiuntivo nella direzione di $B_0$, la cui ampiezza varia linearmente con la posizione lungo un’asse
scelto.

<img src="./images/fig_4_16_p78.png" alt="Figura pagina 78" style="width:100%;">

*Figura 4.16. Aggiunta di un campo magnetico variabile lungo l`asse $x$.*

L’applicazione di un gradiente di campo $G_x = dB_z/dx$ nella direzione $x$ per esempio fa si che l’intensità del
campo magnetico vari come $B_z(x)= B_0 +x G_x$ (*Figura 4.16*).

<img src="./images/fig_4_17_p79.png" alt="Figura pagina 79" style="width:100%;">

*Figura 4.17. Codifica del FID in funzione della posizione spaziale dei nuclei di idrogeno, con gradiente attivo.*

La *Figura 4.17* mostra come varia la frequenza del segnale emesso dalle varie bottiglie di acqua, in funzione
della loro posizione spaziale: la bottiglia che è influenzata da un campo $B < B_0$ (bottiglia 1) emette un
segnale con frequenza $\omega < \omega _0$. Analogamente, il contenuto della bottiglia 3, emette un segnale con
frequenza  $\omega > \omega _0$ mentre per la bottiglia 2 la frequenza è $\omega$. Il segnale risultante è dato dalla somma dei tre segnali. Da notare, inoltre, come l’ampiezza dei tre segnali sia diverso a seconda della quantità di acqua
presente nelle bottiglie (dipende infatti dal numero di nuclei di idrogeno - densità protonica).

### 4.2.2 Sistema di gradienti per la formazione dell’immagine

Un sistema per immagini contiene tre bobine che generano i gradienti lungo i tre assi ortogonali $x,y,z$.
Questi assi sono fissi nel magnete e l’origine è al centro del magnete, mentre il campo $B_0$ è per convenzione
lungo $z$.

L’unità di misura dei gradienti è il Tesla per metro (T/m). I gradienti variano tipicamente da 0.1 mT/m a 5
mT/m; stiamo quindi parlando di piccolissimi cambiamenti di campo dovuti ai gradienti rispetto a $B_0$.
La discriminazione spaziale è effettuata attivando opportunamente i tre gradienti, così da ottenere tre tipi
di codifica, lungo le tre direzioni spaziali: 
- codifica di frequenza 
- eccitazione selettiva 
- codifica di fase.


1. La codifica di frequenza sfrutta la proprietà che la frequenza di risonanza nella RM è direttamente
proporzionale all’intensità del campo magnetico. Quando applichiamo un gradiente (ad esempio lungo x)
abbiamo una frequenza di risonanza che è funzione della posizione lungo la direzione del gradiente, ovvero
$$
\omega (x) = \gamma (B_0 + x G_x)
$$
Nella tecnica di codifica di frequenza prima viene applicato un impulso a 90° per eccitare gli spin, e poi è
attivato il gradiente di codifica e si acquisisce il segnale di RM in presenza del gradiente acceso.
Conoscendo l’intensità del gradiente, dalla frequenza del segnale osservato si può risalire alla posizione
dell’oggetto lungo la direzione del gradiente del campo. Il gradiente è dunque usato per codificare
informazioni spaziali in frequenza del segnale di RM.
L’ampiezza del segnale è proporzionale al numero di spin in quella posizione. Per ottenere
informazioni spaziali da questo segnale composto occore fare un’analisi in frequenza del segnale,
così da vedere la quantità di segnale presente ad ogni frequenza in un intorno della frequenza
fondamentale di risonanza $\omega _0 = \gamma B_0$.

2. Con la codifica di selezione della fetta l’eccitazione di RM, e dunque il segnale, è limitata ad
una fetta scelta in un campione o paziente. Si ottiene applicando un impulso a 90° insieme ad un
gradiente “Slice Selection Gradient” perpendicolare alla fetta desiderata. Per acquisire
l’immagine di una fetta nel piano $xy$, occorre applicare il “Slice Selection Gradient” nella
direzione $z$. L’effetto del gradiente è dunque quello di rendere la frequenza di risonanza una
funzione della posizione lungo la direzione $z$; cioè
$$
\omega (z) = \gamma (B_0 + z G_z)
$$

<img src="./images/fig_4_18_p80.png" alt="Figura pagina 80" style="width:100%;">

*Figura 4.18. Eccitazione selettiva di una fetta.*

L’impulso a 90° è detto “selective pulse” perché la sua ampiezza è modulata in modo tale da
contenere uno stretto intervallo di frequenze vicine alla frequenza fondamentale $\omega _0 =\gamma B_0$: solo
quegli spin la cui frequenza di risonanza appartiene a questo intervallo saranno eccitati. La
larghezza della fetta $\Delta Z$ e’ data da (vedi *Figura 4.18*):

$$
\Delta Z = \Delta \omega / \gamma G_z
$$

dove $\Delta \omega$ è l’intervallo delle frequenze contenute nell’impulso a 90° selettivo e $G_z$
è l’intensità del gradiente applicato per la selezione di una fetta. $\Delta \omega$ è legato alla forma e alla durata
dell’impulso. Se consideriamo un impulso di forma gaussiana, $\Delta \omega = 2 \pi/ \Delta t$, dove $\Delta t$ è
l’ampiezza a metà altezza dell’impulso. La fetta può essere fatta più sottile diminuendo la
larghezza di banda dell’impulso (cioè aumentandone la durata) o aumentando l’intensità di $G_z$.

3. La codifica di fase è così detta perché la fase della precessione della magnetizzazione viene
resa dipendente dalla posizione lungo la direzione del gradiente. Se ad esempio viene applicato
un impulso a 90° ad una colonna di spin seguito da un gradiente di codifica di fase, gli spin
precederanno a differenti velocità defasandosi gli uni rispetto agli altri. Quando il gradiente viene
disattivato, gli spin sentono lo stesso campo magnetico $B_0$ e precedono tutti alla stessa frequenza
ma mantengono uno sfasamento che dipende dalla posizione lungo la direzione di codifica di fase.
In una data posizione lo sfasamento dipende dalla grandezza del gradiente di codifica di fase
applicato, secondo la formula:
$$
\Phi(y)
=
\int_{0}^{T}\omega(y)\,dt
=
\gamma y\int_{0}^{T}G_y\,dt
$$
dove $T$ è il tempo per cui il gradiente di codifica di fase è acceso e $G_y$ è l’ampiezza di tale
gradiente.

Abbiamo dunque visto come l’applicazione di gradienti di campo magnetico possa produrre un
profilo dell’oggetto $S(x)$ lungo un’asse parallelo al gradiente di lettura (l’asse $x$ nel nostro caso).
Il profilo è equivalente alla somma dei segnali dai vettori di magnetizzazione nelle colonne
perpendicolari all’asse $x$ e contenuti nella fetta selezionata. Abbiamo anche visto come possiamo
codificare l’informazione nella direzione ortogonale modificando la fase del segnale $S(x)$ con un
gradiente (detto gradiente di fase) applicato prima di quello di lettura (cioè prima del gradiente
lungo $x$). Una sequenza composta da diversi gradi di sfasamento può essere utilizzata per
ricostruire un profilo di ciascuna colonna; possiamo perciò ricostruire un’immagine
bidimensionale.
Riassumendo, la successione di attivazione e disattivazione di dei gradienti (sequenza) per la
codifica spaziale, che permettono la formazione dell’immagine, consiste in:

- Selezione di una fetta ed eccitazione degli spin (intervallo 1 *Figura 4.19*).
- Un phase encoding gradient applicato tra l’eccitazione e il periodo di lettura (intervallo 2 *Figura
4.19*)
- Un gradiente di lettura durante il quale è raccolto il segnale RM (intervallo3 *Figura 4.19*).

Al fine di ottenere l’immagine, questa sequenza è ripetuta più volte, variando ogni volta
l’ampiezza del gradiente di fase, come mostrato nell’esempio di *Figura 4.19*.

<img src="./images/fig_4_19_p82.png" alt="Figura pagina 82" style="width:100%;">

*Figura 4.19. Rappresentazione schematica di una sequenza per la generazione di immagine RM.*

La serie di segnali così acquisiti, vengono opportunamente digitalizzati e memorizzati in una matrice detta
k-spazio (vedi *Figura 4.20*).

<img src="./images/fig_4_20_p82.png" alt="Figura pagina 82" style="width:100%;">

*figura 4.20. Memorizzazione dei segnali acquisiti durante la sequenza.*

### 4.2.3 Il K-Spazio

L’evoluzione di un sistema di spin dopo l’eccitazione è studiata più facilmente nello spazio
reciproco o k-spazio. Tale spazio è in realtà il dominio della trasformata di Fourier dello spazio
ordinario. La relazione tra i due è analoga a quella tra la frequenza angolare ed il tempo. k sta per
numero d’onda $k= 2 \pi /\lambda$, con componenti $K_x$, $K_y$ e $K_z$.

 Un` onda sinusoidale nel k-spazio, di lunghezza d’onda $\lambda = 2 \pi /K$ con la direzione della normale al fronte d’onda coincidente con la direzione di K, nello spazio reale corrisponde ad un punto (vedi *Figura 4.21*).

<img src="./images/fig_4_21_p83.png" alt="Figura pagina 83" style="width:100%;">

*Figura 4.21. Relazione tra il k-spazio e lo spazio immagine.*

Scriviamo ora l’equazione che descrive il segnale come funzione della codifica di fase e della
codifica in frequenza per la sequenza spin-warp (di tipo Gradient echo) di *Figura 4.19*. Se si hanno
$M$ segnali FID, uno per ogni codifica di fase, cioè ciascuno con un diverso valore di ampiezza del
gradiente di fase (tali valori di ampiezza possono essere sia positivi che negativi), e ciascun
segnale (FID) è campionato con $N$ campioni separati da T, otteniamo un insieme bidimensionale
di dati $s(n,m)$ dato da:

$$
s(m,n)
=
e^{-\left(nT+t_d\right)/T_2}
\iint
\rho(x,y)\,
e^{-i\gamma\left(nT G_x x + m t_y G_y y\right)}
\,dx\,dy
$$

$$
0 \leq n \leq N
$$

$$
-\frac{M}{2} \leq m \leq \frac{M}{2}
$$


La (41) è in genere definita come l’equazione dell’immagine RM. Se $M= 256$ e campioniamo
256 punti $t = nT$ per ciascun valore di $m$, allora si avrà come risultato una matrice di $256x256$ n punti.

Applicando questa formula ad una sequenza, possiamo tracciare un cammino nel K-spazio. Ad
esempio nella sequenza Spin Warp ogni codifica di fase ci porta ad un nuovo punto di inizio alla
sinistra del K spazio (vedi *Figura 4.19* e *4.22*), poi quando è presente solo il gradiente di lettura,
che è lungo $x$, si vede che k “viaggia” orizzontalmente da sinistra verso destra con velocità
costante.

<img src="./images/fig_4_22_p84.png" alt="Figura pagina 84" style="width:100%;">

*Figura 4.22. Modalità di riempimento del k-spazio con la sequenza spin-warp.*

Se eseguiamo nella (41) la seguente sostituzione:

$$
k_x = \gamma n T G_x
$$

$$
k_y = \gamma m t_y G_y
$$

e con l’assunzione che il periodo di codifica di fase $t$ ed il periodo di lettura del FID, $nT$, siano
molto più brevi del T2 del materiale, possiamo riscrivere la (41):

$$
s(k_x,k_y)
=
e^{-\left(nT+t_d\right)/T_2}
\iint
\rho(x,y)\,
e^{-i\left(k_xx+k_yy\right)}
\,dx\,dy
$$

Dalla (46) è facile vedere che la matrice dei dati acquisiti $s(k_x,k_y)$ è la Trasformata di Fourier
della funzione $\rho (x,y)$. Perciò, se applichiamo una Trasformata inversa bidimensionale di Fourier
(algoritmicamente: la IFFT) sulla matrice dei dati $s(n,m)$, il risultato sarà l’immagine contente i
valori di $\rho (x,y)$.

E’ possibile quindi ottenere un’immagine della distribuzione di spin campionando il K-spazio e
applicando la trasformata di Fourier. Tutti i metodi di MRI che si basano sull’ applicazione dei
gradienti si distinguono per i diversi modi di acquisire il FIS nel K-spazio.
Nelle immagini di risonanza magnetica, ci sono molti fattori che influenzano il contrasto; tra
questi ci sono i tempi di rilassamento $T_1$, $T_2$, e la densità dei protoni (si parla di immagini $T_1$, $T_2$
e $PD$ pesate). Uno dei più grandi vantaggi è di poter cambiare il contrasto scegliendo particolari
sequenze con i relativi parametri. Enfatizzando un fattore o mescolando diversi fattori in modo
specifico, si può aumentare il contrasto di una certa regione, ed eventualmente mettere in evidenza
una lesione patologica.
In *Figura 4.23, 4.24, 4.25* sono mostrate 3 immagini RM relative alla stessa sezione, ma acquisite con diversi
parametric così da ottenere immagini pesate $T_2$ (T2W), $T_1$ (T1W) o Proton density (PDW).

<img src="./images/fig_4_23_p85.png" alt="Figura pagina 85" style="width:100%;">

*Figura 4.23: esempi di immagini RM: T2W.*

<img src="./images/fig_4_24_p85.png" alt="Figura pagina 85" style="width:100%;">

*Figura 4.24: esempi di immagini RM: T1W.*

<img src="./images/fig_4_25_p85.png" alt="Figura pagina 85" style="width:100%;">

*Figura 4.25: esempi di immagini RM: PDW.*

## 4.3 Strumentazione
Un sistema per la risonanza magnetica ad uso clinico è generalmente costituito dalle seguenti parti
- un magnete, che genera il campo magnetico statico ($B_0$) per allineare i protoni all’asse del campo
stesso;
- un trasmettitore di impulsi RF costituito da una bobina che genera impulsi RF al fine di perturbare
l’allineamento dei protoni a $B_0$;
- un ricevitore di segnali RF costituito da una bobina ricevente l’energia riemessa dai protoni sotto forma
di segnale RM;
- tre bobine per la generazione dei gradienti di campo magnetico, che modificano cioè l’omogeneità del
campo $B_0$ in modo da rendere spazialmente riconoscibile ogni punto;
- un sistema computerizzato per l’amplificazione, la digitalizzazione, e l’elaborazione dei segnali RM,
in modo da comporre l’immagine RM finale.

In figura 4.26 è riportato lo schema a blocchi di un apparecchio di questo tipo.


<!-- Pagina PDF 86 -->

<img src="./images/fig_4_26_p86.png" alt="Figura pagina 86" style="width:100%;">

*Figura 4.26. Schema di uno strumento per MRI.*

### 4.3.1 Il magnete
Attualmente esistono diversi tipi di magnete, che possiedono caratteristiche tecniche differenti, ma anche
costi di acquisto e di gestione diversi. I più utilizzati sono:
- magnete permanente
- magnete resistivo
- magnete superconduttivo.

#### Magnete permanente
E’ formato da blocchi di materiale ad alta memoria magnetica che, una volta magnetizzati, mantengono il
campo magnetico creato nel loro assemblaggio. Magneti di questo tipo riescono a raggiungere campi non
molto elevati: fino a 0.3 T. Hanno l’ulteriore inconveniente di essere molto pesanti (per cui è necessario
installarli in locali che riescano a supportare pesi elevati); inoltre l’omogeneità del campo dipende molto
dall’assemblaggio dei blocchi e dalle variazioni di temperatura ambientale. Tuttavia, questi magneti, hanno
un costo d’acquisto relativamente basso e richiedono bassi costi di manutenzione. Hanno inoltre il
vantaggio di avere un orientamento verticale del campo magnetico principale e, per la loro configurazione
di tipo “aperto”, riducono molto i fenomeni di claustrofobia dei pazienti.

#### Magnete resistivo
Questo magnete può essere considerato come una grossa elettrocalamita, formata da spire di materiale
conduttore di elettricità nelle quali circola costantemente corrente di elevata intensità. Il problema
principale per questo tipo di magnete è dovuto alla grande quantità di calore generata dal passaggio di
corrente nel conduttore, per fenomeni di resistenza elettrica, con conseguente necessità di sistemi di
raffreddamento; inoltre, il consumo di energia elettrica è molto elevato ed i campi magnetici generati sono
di intensità medio-bassa (0.2 - 0.3T). ci sono inoltre problemi di omogeneità del campo magnetico dovuti
alla fluttuazione nel tempo della corrente e agli sbalzi di temperatura. I maggiori vantaggi di questo tipo di
magnete consistono nella configurazione di tipo “aperto”, la semplicità con cui si genera e si annulla il
campo magnetico (basta togliere l’alimentazione elettrica), e i costi, sia per l’acquisto che per la
manutenzione, piuttosto contenuti.

#### Magnete superconduttivo
E’ il tipo di magnete attualmente più utilizzato, grazie agli ottimi livelli di intensità, omogeneità e stabilità
temporale del campo magnetico statico. I vantaggi principali di questo tipo di magneti consistono: nella
possibilità di raggiungere campi magnetici elevati (>0.5 T), nell’elevata stabilità temporale del campo, e
nella possibilità di avere un campo omogeneo anche su grandi volumi, così da poter acquisire con campi di
vista elevati (fino a $50 cm^3$).
Il magnete superconduttivo si basa sul principio per cui in alcuni materiali, detti appunto superconduttori,
in particolari condizioni di temperatura (vicina allo 0 assoluto) la corrente elettrica può passare con una
resistenza praticamente nulla. In tal modo, la corrente che attraversa le spire del superconduttore genera un
campo magnetico di altissima intensità (fino a 7 T e oltre), indefinitivamente, fino a che le condizioni della
temperatura prossima allo zero sono mantenute.
I problemi principali di questo tipo di magneti consistono in: la configurazione di tipo “chiuso”, ad un costo
sia di acquisto che di gestione molto elevati; infatti, per la creazione dell’ambiente freddo nel quale alloggia
il materiale superconduttore, si utilizzano criogeni, come elio e azoto. Tali liquidi vengono periodicamente
reintegrati nella camera del superconduttore in modo da garantire una temperatura costante (circa 4K, cioè
-269°C).

#### Omogeneità di campo magnetico
Uno dei requisiti fondamentali del campo magnetico generato dal magnete consiste nell’omogeneità del
campo stesso. Una bassa omogeneità di campo causerà la formazione di immagini con scarsa qualità perché
i protoni del campione in esame, non trovandosi alla stessa intensità di campo magnetico, non risentiranno
tutti dell’impulso RF che agirà invece selettivamente sui protoni che precedono alla frequenza di risonanza
stabilita. L’omogeneità di campo magnetico si misura in parti per milione (ppm); la bontà del magnete è
appunto caratterizzata dall’avere disomogeneità piuttosto contenute, di poche ppm.
Le apparecchiature di RM sono dotate di sistemi, detti “shims”, che controllano l’omogeneità del campo
magnetico statico; questi si dividono in passivi e attivi. Lo shimming passivo è realizzato in fase di
costruzione del magnete e corregge le disomogneità del campo dovute alla presenza delle strutture
metalliche utilizzate per la realizzazione del magnete stesso. Lo shimming attivo è invece un sistema di
correzione delle disomogeneità del campo che sfrutta bobine poste internamente all’apparecchio (bobine
di shimming) al fine di correggere con estrema precisione le disomogneneità nel
volume centrale al magnete.

### 4.3.2 Bobine a radiofrequenza

Le bobine RF sono delle antenne utilizzate per emettere i segnali a radiofrequenza necessari a perturbare
l’allineamento dei protoni al campo magnetico $B_0$ (bobine di trasmissione) e a ricevere i segnali emessi dai
tessuti durante la fase di rilassamento dei protoni (bobine di ricezione). Quest’ultimo tipo di antenne (in
ricezione) sono di grandezza e morfologia variabili in relazione al distretto corporeo da analizzare.

#### Bobine di trasmissione
Potenzialmente, ogni bobina o antenna può sia trasmettere che ricevere i segnali RF, e infatti così avveniva
nei primi tomografi; attualmente, nei moderni sistemi RM, esiste un’unica bobina che trasmette i segnali
RF, fissata nella parte interna del magnete. Tale antenna è denominata body coil (bobina del corpo) ed è
solitamente usata in trasmissione, mentre è utilizzata sia in trasmissione che in ricezione quando si devono
studiare grandi volumi corporei (da qui il termine Body).

#### Bobine di ricezione
Esistono ora in commercio moltissimi tipi di bobine di ricezione, diverse per la forma, la filosofia di
costruzione, e la qualità della ricezione, in funzione del tipo di distretto anatomico da analizzare. Per quanto
riguarda l’acquisizione di segnali dal sistema cardiovascolare, le bobine di ricezione si possono distinguere
in tre grandi "famiglie": bobine di volume, di superficie e phased array.

- **Bobine di volume.** Hanno solitamente la forma di un cilindro cavo, al cui interno viene posizionata la
struttura da esaminare. Possiedono un’eccellente omogeneità di ricezione interna ed aumentano
notevolmente il rapporto segnale-rumore quanto più vengono “riempite” dall’oggetto in esame (senza però
toccarle). Per questo, esistono bobine di volume di grandezza variabile, in rapporto alle parti corporee da
esaminare (cranio, collo, addome, ginocchio, ecc.). Attualmente, le bobine di volume più utilizzate, sono
quelle dette “a gabbia di uccello” (birdcage) costituite da una serie di barre, ciascuna delle quali riceve il
segnale dalla parte del campione in esame ad essa più vicina.
- **Bobine di superficie.** Hanno una configurazione tale da consentire loro di ricevere il segnale dalle strutture
superficiali contigue alla bobina; infatti, aumentando la distanza tra il campione e la bobina, il segnale si
riduce in modo quadratico. Con questo tipo di bobine è possibile acquisire immagini con piccoli campi di
vista, mantenendo tuttavia alti rapporti segnale-rumore (per esempio, per l’acquisizione del distretto
carotideo). Un’altra caratteristica delle bobine di superficie è la loro morfologia che è variabile
relativamente alla zona corporea per cui sono state specificamente costruite (bobine piatte, bobine circolari,
bobine avvolgenti, ecc.). In figura è mostrato un esempio di bobina di superficie, utilizzata appunto per la
ricezione di segnali RF dal collo.
- **Phased array.** Sono antenne costituite da più unità, disposte in modo opportuno; ciascuna unità riceve
indipendentemente il segnale dai segmenti del campione di loro pertinenza , esaminato con un ritardo
prestabilito. Successivamente, i segnali ricevuti da ogni singola bobina vengono elaborati in modo da
formare un’immagine globale, data dalla somma opportuna delle singole immagini ricevute da ogni bobina.
In questo modo si ottengono immagini con un alto rapporto segnale-rumore insieme ad un grande campo
di vista: infatti la risoluzione spaziale è determinata dalle singole unità, mentre il campo di vista totale
dell’immagine è dato dalla somma dei campi di vista delle singole unità della bobina. 

### 4.3.3 Gradienti di campo

I gradienti di campo sono delle bobine che vengono accese e spente frequentemente al fine di creare campi
magnetici variabili nel tempo e nello spazio Le bobine dei gradienti sono posizionate esternamente al
magnete. Con l’opportuna attivazione e disattivazione dei gradienti, infatti, si ottengono le tre codifiche spaziali
(selezione della fetta, codifica di fase e codifica di frequenza) al fine di rendere riconoscibile la posizione
di ogni punto del campione, caratterizzandolo con una propria intensità di campo magnetico. I gradienti in
un tomografo sono tre, ognuno orientato secondo una delle tre direzioni spaziali ($x,y,z$ di cui $z$ solitamente
si definisce parallela a $B_0$), tanto da rendere possibile la selezione di sezioni assiali, sagittali e coronali.
Inoltre, dalla combinazione dei gradienti tra loro, è possibile effettuare scansioni secondo qualsiasi altro
piano nello spazio, oltre ai tre piani ortogonali.

### 4.3.4 Computer

Il computer in un sistema RM costituisce il centro dei comandi e di controllo di tutti i componenti del
tomografo stesso. Infatti è il computer che gestisce tutte le funzioni richieste per la generazione di immagini
RM: dalla gestione delle forme d’onda RF e l’ accensione e spegnimento degli impulsi RF, alla gestione
dei gradienti e dell’acquisizione dei dati, alla manipolazione, alla memorizzazione, ricerca e presentazione
dei dati finali.
Oltre al computer, è presente anche un array-processor che ha il compito di svolgere quei calcoli che
richiedono un’alta velocità, come per esempio il calcolo della Fast Fourier Transform, FFT.
I Driver, permettono la memorizzazione delle immagini acquisite in dispositivi di memoria di massa, come
per esempio i dischi magneto-ottici o i DVD.