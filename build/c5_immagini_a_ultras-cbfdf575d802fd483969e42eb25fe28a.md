# Capitolo 5: Immagini A Ultrasuoni

<!-- Estratto da: Appunti - Principi fisici ImmaginiBiomediche.pdf, pagine 90-101 -->

<!-- Pagina PDF 90 -->

Le tecniche ultrasonografiche sono grandemente utilizzate in Medicina per diversi motivi:
completa innocuità per il paziente. A differenza di quanto avviene con le tecniche che utilizzano radiazioni
ionizzanti, gli ultrasuoni possono consentire misure prolungate nel tempo (monitoraggio) anche in pazienti
a rischio, come le donne in stato di gravidanza;
ottima risoluzione temporale. L’acquisizione di immagini a ultrasuoni è sufficientemente veloce da
consentire la documentazione di fenomeni rapidi, come la contrazione cardiaca: anche i movimenti più
rapidi presenti nel corpo umano, come l’apertura e la chiusura di valvole cardiache, possono essere “visti”.
La formazione delle immagini ultrasoniche segue un principio diverso da quelli utilizzati dalla radiografia,
dalla scintigrafia o dalla risonanza magnetica; infatti, la tecnica ecografica è una modalità di imaging in
riflessione e diffusione generate da interfacce acustiche.
Tale modalità è resa possibile dalla relativamente bassa velocità di propagazione degli ultrasuoni che è di
circa 1500 m/s. Ciò significa che il tempo di andata e ritorno per raggiungere una profondità nel corpo di
25 cm è di circa 333 μsec. Pertanto, le riflessioni da strutture poste lungo il percorso ultrasonico possono
essere visualizzate ricorrendo a circuiti elettronici di processamento convenzionali. Ciò è in netta
contrapposizione con la tecnica a raggi X, dove l’energia viaggia alle velocità della luce, 3x108 m/s. A
questa velocità, si richiederebbero circuiti elettronici operanti con tempi dell’ordine del picosecondo per
distinguere le riflessioni dalle varie profondità nel tessuto. A causa di tale limitazione, i raggi X sono usati
solo in trasmissione. Un'altra caratteristica fondamentale della tecnica ultrasonica è la possibilità di
acquisire informazioni tridimensionali. Infatti, l’onda emessa da un trasduttore ultrasonico può essere
rappresentata con un’onda piana e quindi descritta in due dimensioni - risoluzione laterale-; la terza
coordinata è la profondità di indagine, ovvero il tempo di propagazione dell’onda. Quindi ciascun impulso
ricevuto dal trasduttore convoglia la riflettività di un oggetto in tre dimensioni.

## 5.1 Principi fisici

Gli ultrasuoni (US) possono essere definiti come suoni oltre la banda di percezione dell’uomo (quindi a
frequenze maggiori della banda 16-20KHz). Sono costituiti da onde elastiche, di compressione e
rarefazione, longitudinali, che trasferiscono energia meccanica e richiedono quindi un mezzo per la loro
propagazione. Ogni mezzo può essere considerato composto da un grande numero di particelle, che
normalmente sono a riposo e che quando sono perturbate da un’onda ultrasonica oscillano attorno alla loro
posizione di equilibrio. La velocità di propagazione dell’ultrasuono dipende dalla natura del mezzo, e cioè:
l’accoppiamento più o meno stretto delle particelle e la loro inerzia (quindi l’elasticità del mezzo).
L’ecocardiografia si basa sulle caratteristiche di riflettività delle disomogeneità biologiche che
costituiscono il bersaglio. Naturalmente, affinchè si generi l’immagine per riflessione, è necessario che le
disomogeneità biologiche producano modificazioni acustiche in grado di generare un’onda riflessa. Per
comprendere il significato di disomogeneità acustica, è utile introdurre alcuni delle leggi che regolano
l’interazione tra onda acustica e tessuti biologici. Dal punto di vista ultrasonografico i tessuti biologici sono
modellati come mezzi debolmente disomogenei, le cui disomogeneità hanno dimensioni variabili da
qualche micron a valori dell’ordine dei centimetri.

Le disomogeneità dei tessuti dal punto di vista ultrasonografico possono essere descritte mediante due
grandezze misurabili: l’impedenza acustica e la dimensione (in rapporto con la lunghezza d’onda).

### 5.1.1 Impedenza acustica

L’impedenza acustica è un parametro che riassume le proprietà ultrasonografiche del tessuto biologico.
L’impedenza acustica è definita con la seguente relazione:

$$
Z = \rho v 
$$

dove $\rho$ rappresenta la densità del mezzo e $v$ la velocità degli ultrasuoni nel mezzo. Valori tipici di $Z$ sono
riportati in Tabella 5.1. Per quanto riguarda l’imaging ultrasonografico è importante la variazione di
impedenza acustica, ovvero la differenza tra l’impedenza della disomogeneità e il mezzo circostante.
Infatti, l’entità della riflessione che si genera tra due mezzi (interfaccia acustica) è proporzionale alla
differenza di impedenza acustica.

| Mezzo | $\rho$ ($\mathrm{kg/m^3}$) | $v$ ($\mathrm{m/s}$) | $Z$ ($\mathrm{kg/(m^2\,s)}$) | Attenuazione ($\mathrm{dB/(cm\,MHz)}$) |
|---|---:|---:|---:|---:|
| Aria | 1.3 | 330 | 429 | $>10$ |
| Acqua | 1000 | 1490 | $1.5\times10^6$ | 0.002 |
| Sangue | 1030 | 1570 | $1.6\times10^6$ | 0.18 |
| Tessuto adiposo | 900 | 1450 | $1.3\times10^6$ | 0.6 |
| Muscolo | 1080 | 1585 | $1.7\times10^6$ | 1.5 |
| Polmone | 220 | 900 | $0.2\times10^6$ | 30 |
| Osso | 1850 | 3600 | $7.4\times10^6$ | 8 |

*Tabella 5.1. Densità $\rho$, velocità di propagazione $v$, impedenza acustica $Z$ e attenuazione di alcuni materiali biologici.*

### 5.1.2 Scattering e riflessione

Quando un’onda ultrasonica si propaga attraverso un tessuto biologico, l’interazione con le disomogeneità
del tessuto è regolata dal rapporto tra la lunghezza d’onda e le dimensioni delle disomogeneità. La
lunghezza d’onda è il parametro che mette in relazione la frequenza $f$ di emissione del trasduttore con la
velocità $v$ di propagazione dell’onda ultrasonica. Tale relazione è data da:

$$
\lambda = v/f
$$

Quindi, a parità di velocità $v$ (e quindi per uno stesso tessuto), maggiore è la frequenza dell’onda emessa e
minore è la lunghezza d’onda. I tessuti biologici hanno valori di velocità che oscillano di poco nell’intorno
della velocità media che è 1500 m/sec, ad eccezione del tessuto osseo (v=3600 m/sec), il quale per sua
natura assomiglia più ad un materiale solido, anzichè liquido (vedi Tabella 5.1). A seconda che la lunghezza
d’onda sia maggiore o minore della dimensione della disomogeneità, l’onda riflessa ha caratteristiche
differenti.

A parità di dimensioni della disomogeneità, l’ampiezza dell’eco generato è tanto maggiore quanto più
elevato è il salto in impedenza acustica. D’altra parte, riducendo la dimensione della disomogeneità a valori
inferiori alla lunghezza d’onda, anche l’eco ridurrà la sua ampiezza.
L’interfaccia sangue-muscolo, pur avendo un basso salto di impedenza acustica, viene rappresentata con
una tonalità di grigio tendente al bianco (massima ampiezza) perchè è un riflettore speculare. Viceversa
una microcalcificazione, pur avendo un salto elevato in impedenza acustica, viene rappresentata con una
bassa tonalità di grigio perchè è un riflettore di Rayleigh.

#### Riflettori di Rayleigh.
Il fenomeno dello scattering è causato dalla re-irradiazione dell’onda ultrasonica per effetto delle
disomogeneità dei tessuti, le cui dimensioni sono minori della lunghezza d’onda. Questo tipo di scattering
è anche detto ‘scattering di Rayleigh’. Il termine re-irradiazione indica che la disomogeneità può essere
considerata come una nuova sorgente di ultrasuoni, con emissione isotropica (cioè in modo uniformemente
distribuito su tutto lo spazio circostante). Il fenomeno di scattering ultrasonico è analogo alla diffusione
della luce solare da parte di particelle sospese. La caratteristica peculiare dei diffusori di Rayleigh in
ecografia, è la loro indipendenza dalla orientazione, per cui l’onda diffusa, seppur di debole intensità, può
essere captata dal trasduttore ovunque esso sia posizionato. L’onda retrodiffusa verso il trasduttore è
conosciuta con il nome di backscatter. In *Figura 5.1* è rappresentata la somma lineare sulla superficie di un
trasduttore di echi di backscatter generati da diffusori di dimensioni inferiori alla lunghezza d’onda.

<img src="./images/fig_5_01_p93.png" alt="Figura pagina 93" style="width:100%;">

*Figura 5.1. Somma di onde generate da più diffusori, sulla superficie di un trasduttore.*

I riflettori di Rayleigh sono rappresentati da strutture biologiche di dimensioni inferiori alla lunghezza
dell’onda. Per esempio, per una sorgente di emissione di 3.5 MHz, a cui corrisponde una lunghezza d’onda
$\lambda \approx 0.3$ mm, le disomogeneità responsabili della diffusione sono costituite dalla matrice extracellulare di
collagene che riveste la fibra miocardica e dai vasi capillari.Nell’immagine ecocardiografica i riflettori di
Rayleigh sono responsabili del pattern di livelli di grigio in corrispondenza della parete miocardica.

#### Riflettori speculari.
Il fenomeno della riflessione si ha per lunghezze d’onda minori della dimensione della disomogeneità:
l’onda incidente viene riflessa sotto di angolo uguale a quello dell’onda incidente secondo le leggi
dell’ottica geometrica. Le strutture che rispondono a tali requisiti sono conosciute con il termine ‘riflettori
speculari’. In ecocardiografia i principali riflettori speculari sono i contorni delle cavità, la parete epicardica
e le pareti dei vasi. Il loro contributo è determinante nel formare l’immagine anatomica.

#### Attenuazione
L’attenuazione è causata da fenomeni di assorbimento dovuto alla trasformazione di energia acustica in
energia termica, da fenomeni di scattering dei tessuti e da fenomeni diffrattivi del trasduttore, i quali
provocano l’allargamento del fascio ultrasonico con la distanza. Una formula sperimentale per descrivere
l’attenuazione è la seguente:

$$
A = A_0 e^{-\mu x}
$$

dove $\mu$ è il coefficiente di attenuazione e $x$ è la distanza di propagazione nel mezzo. I liquidi presentano
una debole attenuazione, i tessuti molli hanno un’attenuazione intermedia, mentre l’osso presenta
un’attenuazione molto elevata (vedi tabella 5.1). Il fenomeno dell’attenuazione delimita la massima
frequenza che può essere impiegata in un esame; infatti in generale il coefficiente di attenuazione è una
funzione crescente della frequenza, per cui il suo effetto è tanto maggiore quanto più elevata è la frequenza.
D’altra parte, come vedremo a proposito del trasduttore, frequenze tanto maggiori hanno minore effetto
diffrattivo e quindi una migliore risoluzione laterale.

## 5.2 Strumentazione
Una generica macchina per indagini ecografiche può essere schematizzata mediante il seguente schema a
blocchi di *Figura 5.2*.

<img src="./images/image_5_2.png" alt="Figura pagina 93" style="width:100%;">

*Figura 5.2: schema di uno strumento ecografico*

### 5.2.1 Il trasduttore

Il trasduttore è costituito da un cristallo piezoelettrico che ha la proprietà di contrarsi ed espandersi se
sottoposto ad un campo elettrico. Eccitando quindi con un opportuno segnale il cristallo è possibile ottenere
la voluta conversione di energia elettrica in energia meccanica sotto forma di onde sonore ed ottenere quindi
l'emissione di un fascio ultrasonico di frequenza pari alla frequenza di vibrazione del cristallo. Le frequenze
utilizzate nella diagnostica ultrasonica variano da 2 a 15 MHz, le frequenze più basse sono utilizzate dove
si ha necessità di una elevata penetrazione del fascio ultrasonico (Infatti l'attenuazione dello stesso dipende
quadraticamente dalla frequenza) come ad esempio nelle indagini addominali dove la penetrazione richiesta
può raggiungere la decina di centimetri e più.
Le frequenze più alte consentono una penetrazione minore, ma anche una maggiore risoluzione grazie alla
minore lunghezza d' onda e sono utilizzate per l'analisi di strutture superficiali come ad esempio i vasi
superficiali e l' occhio.

#### Forma del fascio ultrasonico e focalizzazione
Supponendo di avere un cristallo piezoelettrico con superficie piana la forma del fascio emesso può essere
schematizzata come indicato in *Figura 5.3*.

<img src="./images/image_5_3.png" alt="Figura pagina 93" style="width:100%;">

*Figura 5.3: forma del fascio per un trasduttore con superficie piana.*

È possibile individuare due zone la prima delle quali, detta campo vicino, è caratterizzata da una larghezza
del fascio pressoché costante mentre nella seconda, detta campo lontano, si ha una divergenza del fascio.
Come si può vedere dalla figura l'estensione della zona di campo vicino è data dall'espressione

$$
T = \frac{d^2}{4\lambda}
$$

dove $d$ è il diametro del trasduttore e $\lambda$ è la lunghezza d' onda. In questo modo però la larghezza del fascio
non è mai minore del diametro del trasduttore e quindi per diminuirla in modo da aumentare la risoluzione
laterale si ricorre alla focalizzazione. Infatti, non è possibile ridurre la larghezza del fascio diminuendo oltre
certi limiti le dimensioni del trasduttore in quanto in questo modo si riduce l'estensione della zona di campo
vicino ed aumenta la divergenza nella zona di campo lontano. Questi effetti potrebbero venire compensati
con una riduzione della lunghezza d' onda ma in questo caso si avrebbe una maggiore attenuazione del
fascio. Si ricorre quindi alla focalizzazione che può essere fissa (ottenuta mediante lenti acustiche) o
elettronica come si vedrà meglio in seguito.

La forma del fascio in un trasduttore focalizzato nel quale la focalizzazione è ottenuta sagomando
opportunamente la superficie emittente o ponendo davanti alla superficie piana una lente acustica è quella
rappresentata nella *Figura 5.4*. Si vede che si ha un primo tratto in cui vi è un restringimento del fascio fino
ad una dimensione minima in corrispondenza del fuoco. Questa dimensione, nel caso di trasduttori
focalizzati, è data da

$$
A = a\frac{\lambda}{d}
$$

dove $d$ è il diametro del trasduttore, $\lambda$ è la lunghezza d' onda ed $a$ è una costante di proporzionalità, e cioè
è tanto più piccola quanto più grande è il diametro del trasduttore e minore è la lunghezza d' onda. Si vede
che il punto focale si trova ad una distanza dal trasduttore minore rispetto a quella corrispondente all'
estensione della zona di campo vicino per un trasduttore piano delle stesse dimensioni e inoltre, oltrepassato
il punto focale, il fascio diverge rapidamente.

<img src="./images/image_5_4.png" alt="Figura pagina 93" style="width:100%;">

*Figura 5.4: forma del fascio acustico per un trasduttore focalizzato*


L' ampiezza della zona focale che si estende nell' intorno del fuoco stesso è data da
$$
F = b\frac{\lambda}{d^2}
$$

dove $d$ è il diametro del trasduttore, $\lambda$ è la lunghezza d' onda e $b$ è una costante di proporzionalità. Come si
può vedere l'ampiezza della zona focale si riduce rapidamente all' aumentare delle dimensioni del
trasduttore. 

Il punto focale non coincide in genere con il centro di curvatura della superficie del trasduttore
in quanto si trova più vicino alla superficie del trasduttore stesso, ma tende a coincidere con il centro di
curvatura all' aumentare del grado di focalizzazione definito come segue:
- Focalizzazione debole $R/T > 1/2$
- Focalizzazione media $1/2 \pi < R/T < 1/2$
- Focalizzazione forte $R/T < 1/2 \pi$

dove $R$ è il raggio di curvatura della superficie del trasduttore e $T$ è l'estensione della zona di campo vicino
del corrispondente trasduttore piano (vedi *Figura 5.3*). Se ci si trova nel caso di focalizzazione forte il centro
di curvatura coincide approssimativamente con il fuoco acustico.

#### Parametri del trasduttore
Vi sono alcuni parametri che caratterizzano un particolare tipo di trasduttore ultrasonico che devono essere
presi in considerazione nella progettazione di un’apparecchiatura con determinate caratteristiche.

##### Risoluzione Assiale
Con risoluzione si intende la capacità di distinguere oggetti vicini tra loro come oggetti separati e quindi la
capacità di riprodurre fedelmente le immagini. La risoluzione assiale è quindi definita come la minima
distanza in direzione assiale (cioè quella di propagazione dell'onda ultrasonica) alla quale due corpi
producono echi tra loro distinguibili. La risoluzione assiale dipende dalla durata dell'impulso e quindi per
ottenere una elevata risoluzione si deve utilizzare una elevata banda ed una elevata frequenza
compatibilmente con la profondità di penetrazione necessaria.

##### Risoluzione Laterale
Analogamente per risoluzione laterale si intende la capacità di distinguere due oggetti che si trovano vicini
in direzione perpendicolare alla direzione di propagazione. La risoluzione laterale può essere distinta in
risoluzione azimutale e risoluzione in elevazione.
Per risoluzione azimutale si intende quella relativa alla direzione corrispondente alla scansione e cioè
giacente sul piano di scansione (ed ortogonale all' asse del fascio).
Per risoluzione in elevazione si intende invece quella relativa alla direzione ortogonale al piano di scansione
come si può vedere dalla *Figura 5.5*. Nel caso di un array lineare di trasduttori la risoluzione azimutale è
controllata dalla focalizzazione ottenuta per mezzo di opportuni ritardi applicati al segnale relativo a ciascun
elemento dell'array mentre la risoluzione in elevazione è controllata dalla focalizzazione ottenuta con una
lente acustica a fuoco fisso, in genere quindi i punti focali azimutali ed in elevazione non coincidono.

<img src="./images/image_5_5.png" alt="Figura pagina 93" style="width:100%;">

*Figura 5.5. Definizione di risoluzione azimutale e in elevazione per un trasduttore US.*

##### Fuoco dinamico
Con tale termine si intende l’operazione di focalizzazione elettronica sia in trasmissione che in ricezione
effettuata dal modulo di processamento computerizzato residente nella macchina ecocardiografica. La
novità rispetto alla tecnologia precedente è la possibilità di controllare la formazione del campo ultrasonico
ad ogni punto del mezzo sotto indagine, sia durante l’emissione che durante la ricezione.

#### Generatore impulsi di trasmissione
Serve a generare, dietro comando del circuito di temporizzazione, impulsi di ampiezza e durata opportuna
adatti ad eccitare i cristalli piezoelettrici del trasduttore. Le caratteristiche dell'impulso devono essere tali
da accordarsi alle caratteristiche del cristallo piezoelettrico usato e cioè devono avere una durata tale che la
frequenza fondamentale si accordi con la frequenza di oscillazione del cristallo e devono avere un' ampiezza
tale da ottenere un fascio ultrasonico della potenza voluta che varia a seconda del tipo di trasduttore e dell'
applicazione.

#### Focalizzazione elettronica
La sua funzione consiste nel rifasare opportunamente i segnali provenienti da più trasduttori, che
costituiscono un phased array o un anular array, applicando ad ognuno di essi adeguati ritardi in modo da
ottenere il fuoco acustico in un punto desiderato. È possibile effettuare una focalizzazione dinamica
variando questi ritardi in modo che sia messo a fuoco il punto da cui provengono gli echi in un determinato
istante e quindi "seguire" con il fuoco la propagazione dell'onda ultrasonica in modo da ottenere una
focalizzazione estesa a tutto il campo di esplorazione.
È da notare che fino a questo blocco i vari segnali provenienti da ciascun cristallo restano separati mentre
all' uscita, dopo il rifasamento, vengono inviati ad un sommatore che fornisce un unico segnale
proporzionale all' eco ricevuto.

#### Logica di controllo
La logica di controllo svolge varie funzioni all' interno di un'apparecchiatura ecografica, tra cui la principale
è il controllo della scansione del fascio ultrasonico che risulta differente a seconda che la scansione sia
meccanica od elettronica.

#### Scansione meccanica
Per ottenere l'immagine di una sezione dell'organo in esame è necessario che il fascio ultrasonico compia
una scansione dell' intera zona interessata in modo da poter ricostruire l' immagine ricomponendo numerose
linee di vista (*Figura 5.6*). Nel caso di scansione meccanica il trasduttore emette il fascio ultrasonico e riceve
l'eco (il fascio viene focalizzato attraverso le varie metodiche viste) in un'unica direzione e la scansione
viene affidata ad un motorino che muove meccanicamente il trasduttore con un movimento di tipo rotatorio
od oscillante. È evidente che in questo caso è di fondamentale importanza che la logica di controllo, oltre
a controllare il movimento del motorino, sia in grado di associare con precisione una particolare posizione
del motorino ad una particolare linea di vista in modo da poter ricomporre poi l'immagine in modo corretto
associando ad ogni linea di vista esattamente il segnale che proviene da quella particolare direzione.


<img src="./images/image_5_6.png" alt="Figura pagina 93" style="width:100%;">

*Figura 5.6. Schema di una scansione meccanica.*

#### Scansione elettronica
In questo caso il trasduttore, costituito da un array di trasduttori, non compie movimenti meccanici e la
scansione è ottenuta controllando opportunamente le fasi dei segnali di eccitazione e dei segnali eco ricevuti
in modo da ottenere la scansione desiderata. La scansione può essere sia di tipo settoriale e cioè simile al
caso precedente ottenendo in questo caso immagini a forma di settore circolare (vedi figura 4.7, in alto),
che di tipo lineare eccitando cioè uno o più trasduttori dell' array in modo da muovere il fascio
parallelamente a se stesso ottenendo immagini di forma rettangolare come illustrato schematicamente in

<img src="./images/image_5_7.png" alt="Figura pagina 93" style="width:100%;">

*Figura 5.7. formazione dell’immagine ecografia con scansione elettronica settoriale (in alto) o parallela (in basso).*

È evidente che in questo caso la logica di controllo dovrà selezionare quali cristalli siano da utilizzare per
l’emissisone e controllarne le fasi relative in modo da ottenere la scansione voluta.

La figura 5.8 mostra quattro immagini ecocardiografiche relative a diverse fasi del ciclo cardiaco.

<img src="./images/fig_5_02_p99.png" alt="Figura pagina 99" style="width:100%;">

*Figura 5.8. Esempio di immagini ecocardiografiche.*

#### Generatore di temporizzazione
Questo blocco serve per sincronizzare tutte le varie sezioni dell'apparecchiatura in modo da assicurarne il
corretto funzionamento. Il collegamento con il generatore di impulsi di trasmissione è necessario per far si
che gli istanti di emissione del fascio ultrasonico coincidano con quelli stabiliti dalla logica di controllo in
modo da associare ad ogni linea di vista una particolare emissione ultrasonora. Analogamente si ha la
necessità della temporizzazione nei blocchi di ricezione (Amplificatore, Circuito TGC, Focalizzazione) che
devono ovviamente essere sincronizzati con la trasmissione per effettuare le necessarie elaborazioni del
segnale come verrà spiegato meglio parlando del circuito TGC e della focalizzazione.
Infine, è evidente la necessità delle temporizzazioni nei blocchi relativi alla visualizzazione dell'immagine
(Convertitori, Scan converter, Monitor TV) in quanto è proprio qui che viene fatta l'associazione tra un
segnale ricevuto ed una particolare linea di vista in modo da ricostruire una immagine bidimensionale della
sezione stessa.

#### Amplificatore e Circuito TGC
Il primo serve per amplificare opportunamente i deboli segnali elettrici provenienti dal trasduttore in
ricezione. Infatti quando l'onda ultrasonica attraversa l'interfaccia tra due materiali di diversa impedenza
acustica viene in parte trasmessa ed in parte riflessa e quindi si forma un eco che, una volta raggiunto il
trasduttore, viene da questo trasformato in un segnale elettrico. Questo segnale è generalmente piuttosto
debole e immerso nel rumore che è dovuto a varie cause sia interne che esterne all' apparecchiatura. L'
amplificatore dovrà quindi avere caratteristiche tali da consentire sia un elevato guadagno che un opportuno
filtraggio in modo da ridurre il più possibile il rumore.

Un cenno a parte merita il circuito TGC (Time Gain Compensation), il quale svolge l'importante funzione
della regolazione del guadagno in funzione della profondità di penetrazione del fascio. Infatti sappiamo che
l' onda ultrasonica, propagandosi nel tessuto, subisce una attenuazione tanto maggiore quanto più grande è
il percorso effettuato, perciò gli echi provenienti da tessuti più profondi danno luogo a dei segnali più deboli
rispetto a quelli provenienti da tessuti superficiali e quindi, all'atto della ricostruzione dell'immagine, si
otterrebbe una luminosità decrescente in funzione della profondità (ogni punto dell' immagine ha una
luminosità proporzionale all' intensità del segnale ricevuto). Il circuito TGC controlla il guadagno
dell'amplificatore in modo che l'ampiezza del segnale risultante non dipenda dalla profondità da cui viene
ricevuto l'eco ma solo dalla discontinuità di impedenza acustica.

#### Demodulatore
Il segnale all' uscita del sommatore viene poi inviato al demodulatore che dà in uscita un segnale
proporzionale all' inviluppo del segnale RF e quindi proporzionale all' intensità dell'eco ricevuto. A questo
livello possono essere effettuate alcune elaborazioni sul segnale come ad esempio la compressione
logaritmica che consente di comprimere la dinamica di un segnale quando essa è superiore alla massima
dinamica rappresentabile sullo schermo in modo da poter visualizzare sia gli echi più deboli che quelli più
forti. Altre elaborazioni possono tendere ad esaltare alcune caratteristiche del segnale in modo che il medico
possa evidenziare meglio ciò che gli interessa oppure migliorare la visualizzazione della sezione sotto
esame.

#### Convertitori A/D-D/A e Scan Converter
In questo blocco viene ricostruita l'immagine bidimensionale della sezione esplorata.
Il convertitore A/D effettua una conversione del segnale in uscita dal sommatore (che è proporzionale all'
intensità del fascio) in forma numerica, i dati ottenuti sono quindi memorizzati in una memoria presente
nello Scan Converter. Questa memoria che viene scritta per colonne alla velocità di scansione (ogni colonna
rappresenta l'intensità dell'eco ricevuto lungo una particolare direzione) viene letta per righe ad una velocità
adatta alla presentazione video ed i dati vengono inviati al convertitore D/A che fornisce in uscita il segnale
video adatto a pilotare il monitor TV. È evidente che la dimensione della memoria dello Scan Converter
sarà in relazione con la risoluzione voluta, infatti in un maggior numero di locazioni di memoria sarà
possibile memorizzare le intensità dell'eco relative ad un maggior numero di punti.
È da tener presente però che la massima risoluzione che è ragionevole attendersi da un'apparecchiatura
ecografica è dell' ordine di 0.5 mm e quindi sarà inutile prevedere campionamenti così ravvicinati da
determinare una risoluzione teorica minore di 0.5 mm che comporterebbero solo un incremento delle
dimensioni della memoria e dei costi dell' apparecchiatura senza portare alcun beneficio.

## 5.3 Principi della formazione dell’immagine ecografica

La formazione dell’immagine ecografica avviene sfruttando il fenomeno della riflessione che si forma tra
due mezzi con diversa impedenza acustica. In trasmissione, l’impulso $p(t)$ eccita il trasduttore e questi
emette un’onda ultrasonica; immediatamente dopo la trasmissione, i circuiti di controllo abilitano il
trasduttore a ricevere gli echi generati dalle discontinuità dei tessuti. Infatti, quando il fronte d'onda incontra
una discontinuità, l'onda viene re-irradiata o riflessa in accordo con quanto detto precedentemente. Tale
onda è ricevuta dallo stesso trasduttore e il segnale risultante è processato e visualizzato su uno schermo
secondo differenti modalità. Per effettuare una trattazione teorica semplificata del processo di formazione
delle immagini ultrasoniche, è necessario ricorrere ad un certo numero di approssimazioni. In particolare,
assumiamo che: il diametro, o estensione, del trasduttore sia molto maggiore della lunghezza d'onda. Sotto questa
assunzione l'onda che si propaga può essere considerata come un estensione della superficie del trasduttore
$S(x,y)$. In pratica ignoriamo la diffrazione.

Assumiamo inoltre che l'onda si propaghi con velocità $v$ uniforme su tutto il percorso e il coefficiente di attenuazione $\alpha$ sia uniforme
(in pratica $\alpha$ è il coefficiente di attenuazione mediato su tutti i tessuti attraversati);
il corpo umano possa essere modellato come una distribuzione di scatteratori isotropici con riflettività
$R(x,y,z)$:

Il modulo del segnale risultante, dopo l'operazione di inviluppo da parte della macchina ecografica, è dato
da:

$$
e(t)
=
k
\left|
\iiint
\frac{e^{-2\alpha z}}{z}
\,R(x,y,z)\,S(x,y)\,
p\left(t-\frac{2z}{c}\right)
\,dx\,dy\,dz
\right|
$$

dove:
- $k$ è un fattore di normalizzazione; 
- $e^{-2\alpha z}$ è l'attenuazione del tessuto attraverso la distanza $2z$; 
- $S(x,y)$ tiene conto della forma del fascio nel piano di propagazione; 
- $\tilde{p}\left(t-\frac{2z}{c}\right)$ è l'impulso ricevuto dopo un ritardo $2z/c$ (andata e ritorno nel corpo);
- $\tilde{p}(t)$ è dato dalla convoluzione tra l'impulso elettrico che eccita il trasduttore, la risposta impulsiva del trasduttore e i circuiti di elaborazione; 
- $||$ rappresenta il valore assoluto, che sostituisce l'inviluppo del segnale a radiofrequenza; 
- $1/z$ rappresenta la perdita in dell'onda retrodiffusa, dovuta alla diffrazione per effetto di ciascun scatteratore; 
- $R(x,y,z)$, funzione di riflettività del bersaglio, è assunta essere uno scalare nel senso che non dipende dall'angolo di insonificazione. 

Ciò è vero per strutture che sono piccole rispetto alla lunghezza d'onda e quindi producono uno scattering isotropico. Per strutture speculari, tale assunzione non è valida e il problema deve essere affrontato in termini vettoriali. Inoltre si
assume che il mezzo riflettente sia debolmente scatterante, cioè l’ampiezza delle riflessioni del secondo
ordine e oltre sono ignorate. Ciò è ragionevole per i tessuti i quali hanno una bassa riflettività.

In generale l’equazione precedente dovrebbe contenere il quadrato di $S(x,y)$ per tenere conto dell’effetto
diffrattivo sia in trasmissione che in ricezione. Tuttavia nella (7) trascuriamo l’effetto diffrattivo in
trasmissione, ipotizzando che: 
1. la sorgente ha dimensioni molto maggiori della lunghezza d’onda del
segnale emesso; 
2. il trasduttore è focalizzato.
