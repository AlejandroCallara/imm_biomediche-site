# Capitolo 2: Immagini Radiologiche

<!-- Estratto da: Appunti - Principi fisici ImmaginiBiomediche.pdf, pagine 38-50 -->

<!-- Pagina PDF 38 -->

## 2.1 Principi fisici

Una sorgente di raggi X (ovvero di fotoni ad elevata energia) è ottenuta a seguito della collisione di elettroni
con un opportuno bersaglio. L’energia di collisione viene fornita agli elettroni tramite una d.d.p. L’energia
dipende: dall’energia dell’elettrone, dalla carica del nucleo che costituisce il bersaglio, dalla distanza tra
l'elettrone ed il nucleo. Se il bersaglio è fine, si può supporre che la densità di energia sia costante su tutto
il bersaglio (ovvero il numero di fotoni per unità di area e pesati per l’energia del fotone); l’intensità è
proporzionale al numero atomico Z. L’uniformità dello spettro dipende dalle modalità dell’ interazione. Per
esempio, l’elettrone può dare tutta la sua energia ad un singolo fotone, il quale verrà emesso con energia E,
oppure può produrre più fotoni ognuno con energia E/n. Tale effetto è più pronunciato per un bersaglio
spesso, come è quello usato in pratica, il quale fornisce uno spettro triangolare anziché uniforme (*Figura 2.1*).

<img src="./images/fig_2_01_p38.png" alt="Figura pagina 38" style="width:100%;">

*Figura 2.1. Intensità di fotoni in funzione dell’energia.*

Molti fotoni a bassa energia sono assorbiti prima di lasciare il tubo a raggi X. Si ottiene così uno spettro
filtrato (vedi tratteggio). Tale effetto è benefico, in quanto i fotoni a bassa energia non avrebbero potere
penetrante e quindi causerebbero bruciature sulla pelle, senza peraltro dare contributo all' immagine.
Assumendo valida l’approssimazione secondo cui il fascio di raggi X è prodotto da una sorgente all'infinito,
si possono trascurare le distorsioni dovute alle dimensioni finite della sorgente e quindi supporre che il
fascio di raggi X si propaghi in linea retta. Pertanto i fenomeni di attenuazione del fascio sono dovuti solo
all’interazione con i tessuti attraversati. In particolare il fascio di raggi X è parzialmente assorbito e diffuso,
mentre la rimanente parte di energia viene trasmessa in modo rettilineo verso il rilevatore. Pertanto
l'immagine dell'oggetto in esame è di attenuazione (assorbimento + scattering). Se il numero di fotoni che
interagisce con il mezzo di propagazione (ed è quindi rimosso dal fascio) è $\Delta N$, nello spessore attraversato
$\Delta d$, si ha la seguente relazione:

$
\Delta N = - \mu \Delta d N
$

dove $N$ è il numero totale di fotoni incidenti (nello spessore $\Delta d$) e $\mu$ è una costante di proporzionalità nota
come coefficiente di attenuazione lineare. Con il segno $-$ si intende una perdita di fotoni. La precedente
relazione in forma differenziale diventa:

$$
\int_{N_{\mathrm{in}}}^{N_{\mathrm{out}}} \frac{dN}{N}
=
-\mu \int_{0}^{d} dt
$$

e risolta conduce alla ben nota formula dell’attenuazione:

$$
N_{\mathrm{out}} = N_{\mathrm{in}} e^{-\mu x}
$$

dove $\mu = \mu(x,y,z,E)$ ed $E$ è l’energia del fotone. Per fotoni di energia $E_0$ , che si propagano lungo $z$ per uno
spessore $(l)$ in una porzione di tessuto $(x,y)$, il coefficiente di trasmissione $c_{tr}$ dell'intensità attraverso
l'oggetto è data da:

$$
c_{\mathrm{tr}}(x,y,E_0)
=
\frac{N_{\mathrm{out}}}{N_{\mathrm{in}}}
=
e^{-\int_{0}^{1}\mu(x,y,z,E_0)\,dz}
$$

Se $\mu$ è uniforme sul volume in esame e vale $\mu _0$ per un fotone di energia $E_0$ allora:

$$
t(x,y,E_0)=e^{-\mu_0 l}
$$

Il coefficiente di attenuazione $\mu$ dipende sia dall’energia dei fotoni che attraversano il materiale che dal
numero atomico degli elementi del materiale stesso. Dato che la causa dell’attenuazione è la massa del
materiale, spesso si trova che il coefficiente di attenuazione è normalizzato nel modo seguente: $\mu / \rho$.

Nell' intervallo diagnostico, sotto i 200 Kev, tre meccanismi contribuiscono all' attenuazione:
- scattering coerente
- assorbimento fotoelettrico
- scattering compton

In *Figura 2.2* è riportato il grafico del coefficiente $\mu / \rho$ relativo ai tre meccanismi.

Lo scattering coerente (o di Rayleigh) si ha quando il fascio di raggi X eccita gli atomi i quali riemettono
energia alla stessa lunghezza d'onda. Questo fenomeno è sfruttato in studi di diffrazione a raggi X, dove le
energie dei raggi sono dell’ordine di qualche Kev e quindi le lunghezze d’onda riemesse sono dello stesso
ordine di grandezza delle dimensioni atomiche.

<img src="./images/fig_2_02_p40.png" alt="Figura pagina 40" style="width:100%;">

*Figura 2.2. Valori del coefficiente μ/ρ in funzione dell’energia del fotone*

Tuttavia, nelle applicazioni biomediche, tale forma di interazione non è importante.
L' effetto fotoelettrico si ha quando il fotone X è assorbito interagendo con un elettrone in basso legame. L'
energia cinetica dell’elettrone emesso è dissipata nel materiale. Il posto lasciato vuoto nel guscio è riempito
da un nuovo elettrone, di solito proveniente dal guscio successivo. Tale operazione è accompagnata dall'
emissione di un fotone chiamata radiazione fluorescente.
Questo fenomeno diventa particolarmente importante con materiali che hanno un più alto numero atomico.
Il coefficiente di attenuazione di massa dovuta all'effetto fotoelettrico varia approssimativamente con la
terza potenza del numero atomico del materiale.
La più significativa causa di problemi è lo scattering Compton. Tale effetto consiste nella collisione tra un
fotone X ed un elettrone libero oppure un elettrone che ha perso il legame e si trova in un guscio più esterno.
Per la conservazione dell'energia (il problema deve essere affrontato ricorrendo alla teoria relativistica),
l'elettrone è diffuso ad un angolo α e il fotone è deflesso di un angolo $\alpha$ ad un’energia inferiore (*Figura 2.3*).

<img src="./images/fig_2_03_p40.png" alt="Figura pagina 40" style="width:100%;">

*Figura 2.3. Effetto dello scattering Compton*

Si vede dalla tabella 2.1 che l'energia del fotone scatterato e quella del fotone incidente sono confrontabili,
specialmente per bassi angoli ed energie nell'intervallo diagnostico.
Inoltre, per energie di interesse diagnostico lo scattering è distribuito abbastanza in modo isotropico.
Pertanto, vi sarà anche un numero di fotoni di tipo Compton che riesce a raggiungere il rivelatore con circa
la stessa energia di un fotone diretto e ciò è causa di difficoltà nell'interpretare il coefficiente di attenuazione
del mezzo attraversato.

| Energia del fotone incidente | Angolo di deflessione del fotone, $\theta = 30^\circ$ | $\theta = 60^\circ$ | $\theta = 90^\circ$ | $\theta = 180^\circ$ |
|---:|---:|---:|---:|---:|
| 25 | 24.9 | 24.4 | 24 | 23 |
| 100 | 98.5 | 91 | 84 | 72 |
| 1000 | 794 | 508 | 341 | 205 |

*Tabella 2.1: valori di energia del fotone scatterato, per diversi valori di energia del fotone incidente e dell’angolo di deflessione.*

Dato che ciascuna interazione è indipendente, il coefficiente di attenuazione risultante è la somma dei tre
precedeni effetti. Per esempio, dato che il calcio (nell'osso) ha Z = 20, ciò comporta un significativo effetto
fotoelettrico nella regione a più bassa energia e quindi risulta maggiormente visibile nelle radiografie. Ad
energie più elevate dove l'effetto prevalente è di tipo Compton, il coefficiente μ/ρ diventa confrontabile
con quello degli altri materiali biologici.

## 2.2 Generazione di immagini radiologiche

### 2.2.1 Radiografia convenzionale

La diagnostica radiologica convenzionale include la creazione di immagini radiografiche, che rendano
visibili le modificazioni indotte dal corpo umano sul fascio di raggi X: è su queste immagini che il radiologo
formula la propria diagnosi. Le immagini sono ottenute utilizzando dei sistemi, detti recettori o rivelatori,
capaci di convertire il segnale dei fotoni X, non visibili, in una immagine visibile. Esistono vari tipi di
recettore; tutti formano l’immagine in base all’energia assorbita dal fascio X, ma differiscono dalla tecnica
di conversione dell’immagine radiante in immagine visibile all’occhio umano. I principali recettori sono le
pellicole radiografiche, gli amplificatori di brillanza e i dispositivi utilizzati in radiografia numerica
(radiografia digitale, di cui parleremo nel prossimo paragrafo).
L’efficienza del rivelatore implica una riduzione della dose di radiazioni da impartire al paziente per
ottenere un’immagine valida ai fini della diagnosi. La risoluzione spaziale esprime invece la fedeltà di
trasferimento dell’informazione spaziale (dettaglio) da parte di un sistema di rivelazione; immagini ad alta
risoluzione risultano essere diagnosticamene più valide.
In generale, i rivelatori di radiazione per l’imaging possono essere a conteggio diretto o a integrazione.
I rivelatori a conteggio diretto forniscono le coordinate di ciascun fotone rivelato: per ogni areola del piano
immagine si conosce quindi il numero di fotoni rivelati. I rivelatori ad integrazione forniscono per ogni
areola una grandezza solo mediamente proporzionale al numero dei fotoni rivelati. I rivelatori ad
integrazione producono quindi, rispetto a quelli a conteggio diretto, una ulteriore fluttuazione
nell’immagine oltre a quella intrinseca dovuta alla natura fotonica della radiazione incidente. Dati gli elevati
flussi fotonici, i rivelatori in uso in radiologia sono di tipo integrale, a differenza di quanto avviene
nell’imaging mediante radioisotopi, come vedremo in un prossimo capitolo.
Le immagini radiografiche si possono suddividere in:
- immagini statiche, che forniscono un documento stabile del quadro interno del corpo umano;
- immagini dinamiche, o cinetiche, che rappresentano in tempo reale l’esame eseguito e il movimento
degli organi.

Le immagini statiche sono ottenute impiegando, nella maggior parte degli esami di tipo convenzionale,
delle pellicole radiografiche; la pellicola può anche essere usata come mezzo di visualizzazione di diverse
tecniche di immagine. E’ costituita da due emulsioni fotografiche depositate su entrambe le facce di un
foglio di poliestere o di acetato. L’emulsione è composta di grani di bromuro di argento sospesi in una
gelatina: ciascun grano ha dimensioni dell’ordine di 1 micrometro. La sensibilità della lastra dipende
principalmente dalle dimensioni e dalla densità dei granuli di AgBr e dallo spessore dell’emulsione. La
risoluzione spaziale è invece limitata dalle ionizzazioni che si producono nell’emulsione e dagli elettroni
secondari che si propagano nell’emulsione a partire dal punto di interazione primaria.
Le immagini di tipo dinamico richiedono l’utilizzo di un sistema per radioscopia, basato sull’impiego di un
rivelatore che fornisce luce in corrispondenza dei punti in cui riceve raggi X.

### 2.2.2 Radiografia Digitale

Uno dei vantaggi offerti dalle tecniche digitali è la possibilità di manipolazione delle immagini con tecniche
computerizzate. Un esempio è l’angiografia digitale. Una prima immagine radiologica di un qualunque
organo viene digitalizzata e memorizzata per le elaborazioni successive. Tale immagine è anche chiamata
maschera perchè sarà successivamente sottratta a quelle successive dello stesso organo. La sottrazione
cancella i pixels con livello di grigio inalterato, per cui l’immagine differenza contiene informazioni
sottratte del fondo (tessuti molli, coste, catetere, ecc.) Se una quantità diluita di mezzo di contrasto viene
iniettata nelle carotidi o nel cuore nel momento in cui si ottiene la seconda immagine, l’immagine differenza
sarà in grado di visualizzare più facilmente l’arteria o il ventricolo contenenti il mezzo di contrasto. In
*Figura 2.4* sono riportate due immagini angiografiche rispettivamente prima e durante l’iniezione del mezzo di contrasto. La sottrazione delle due immagini fornisce l’immagine dei vasi coronarici.

<img src="./images/image_2_4.png" alt="Figura pagina 2.4" style="width:100%;">

*Figura 2.4. Immagini angiografiche (a) prima e (b) dopo l’iniezione del mezzo di contrasto*


<!-- Pagina PDF 43 -->

### 2.2.3 La Tomografia Assiale Computerizzata

La Tomografia Assiale Computerizzata è un'indagine radiologica e più in generale una metodologia di
imaging diagnostico, impiegata da circa 20 anni. La TAC, che è sicuramente l'innovazione più originale e
più importante nello sviluppo della Radiologia dopo la comparsa dei Raggi X, ha permesso di riconoscere
lesioni che erano, prima, difficilmente dimostrabili o che richiedevano, per essere diagnosticate una serie
di esami complicati. Una delle limitazioni maggiori dei Raggi X è il fatto che rappresentano la proiezione
dell’informazione lungo un’unica direzione, pertanto, se lungo lo stesso percorso ci sono regioni con
variazioni grandi e piccole di densità elettronica, quelle minori non vengono rilevate. L’unico modo per
evitare che una struttura ostacoli la visione di un’altra è di effettuare la radiografia da ogni possibile
direzione, e questo comporterebbe l’assorbimento da parte del paziente di una dose altissima di radiazioni.
Con la TAC, pur usando la stessa dose di Raggi X necessaria per le radiografie convenzionali, si ottiene
l'immagine di un'intera "fetta" del corpo con una chiarezza cento volte superiore. La TAC consiste in una
particolare applicazione dei Raggi X che, grazie all'impiego di una tecnica di rappresentazione di sottili
spessori del corpo umano (tomografia assiale) e di valutazione statistico -matematica (computerizzata)
dell'assorbimento di tali raggi, consente di rilevare piccole differenze di densità tra i diversi tessuti, che
compongono il corpo. Questo strumento, inventato nel 1972 dall'ingegnere elettronico britannico Godfrey
Hounsfield, nelle prime applicazioni ruota di 180° intorno al corpo del paziente, che deve rimanere
immobile, inviando un sottile fascio di Raggi X in oltre cento punti diversi. Un opportuno numero di
cristalli, disposti in posizioni particolari, serve per raccogliere la radiazione in uscita e per quantificare il
grado di assorbimento della radiazione, e quindi per rilevare lo spessore dei tessuti e delle ossa. I dati
raccolti vengono poi inviati a un computer che li converte in un'immagine significativa. Con questo metodo,
mettendo in movimento contrapposto la sorgente radiogena e il rivelatore, ed usando appositi algoritmi, si
può fornire una mappa dei coefficienti di assorbimento di una sezione trasversale all'asse del corpo in
esame, eliminando le tracce degli altri piani anatomici. I tempi relativamente lunghi di scansione (1 sec) e
d’intervallo tra le scansioni (6-8 sec) hanno limitato, però, l’utilizzo della TAC Standard nello studio di
alcune patologie (tra le quali l’embolia polmonare acuta) in quanto responsabili della scarsa qualità delle
immagini per la presenza di artefatti da movimento.

### 2.2.4 TAC a Spirale

Dalla comparsa della prima apparecchiatura commerciale (Emi Scanner 1971), limitata alla tomografia
computerizzata della testa, le tecnologie connesse alla ricostruzione delle immagini hanno registrato un
impulso straordinario, con perfezionamento sia nell' hardware che nel software. Il tempo di esplorazione é
stato ridotto di almeno un ordine di grandezza estendendo la tecnica a sezioni dell'intero corpo del paziente.
Processi fisiologici non sufficientemente stazionari, come il battito cardiaco e le contrazioni peristaltiche,
inseriscono impulsi spuri (motion artifacts) nell'immagine ricostruita. In prototipi sono stati raggiunti tempi
di esplorazione dell'ordine dei 50 - 100 ms. La TAC a Spirale rappresenta una recente evoluzione della
TAC Standard. Intorno ai primi anni ‘90 i progressi tecnologici hanno reso disponibili tomografi in grado
di effettuare scansioni in tempi più brevi e di eseguire scansioni volumetriche grazie alla rotazione continua
del sistema tubo radiogeno - detettori e al contemporaneo spostamento del tavolo. Questa metodica ha reso
possibile lo studio anche di piccole deformazioni nel tessuto in esame, che prima non erano evidenziate con
la tradizionale TAC. L’esame è meno dipendente dalla collaborazione del paziente, perché è ridotto il tempo
di scansione e può considerarsi ridotta anche la dose di Raggi X impiegata. Queste caratteristiche
permettono l’acquisizione di immagini del torace e dell’addome ad alta definizione libere da artefatti o
distorsioni con indiscutibile miglioramento della sicurezza diagnostica. Inoltre, l’immagine di volume della
TAC a Spirale rende possibile l’evidenziazione di immagini tridimensionali di complesse strutture in un
punto qualsiasi del volume di indagine. I principali vantaggi della tecnica a Spirale rispetto alla tecnica
convenzionale è la qualità dell’immagine: la possibilità di acquisire dati di intere regioni corporee (torace-
addome ecc.) con un'unica apnea da parte del paziente permette di avere immagini complete con un’unica
scansione. La TAC a Spirale permette poi la ricostruzione tridimensionale di organi, distretti e cavità.

### 2.2.5 Modalità di acquisizione in cardiologia

Sono state sviluppate diverse modalità operative concepite per specifiche applicazioni cardiologiche.
Queste includono la modalità di flusso (flow-mode), la modalità cinematografica (cine-mode) e la modalità
volume (volume-mode). La caratteristica più importante in una apparecchiatura di visualizzazione è
rappresentata dalla qualità delle sue immagini, la quale determina la capacità dell’apparecchiatura di
risolvere dettagli degni di interesse e segna i limiti di precisione di tutte le applicazioni quantitative. La
qualità delle immagini può essere rappresentata quantitativamente dalla risoluzione spaziale e dal rumore
delle immagini detto anche risoluzione di contrasto. La modalità di flusso è concepita per campionare una
data serie di tagli ad intervalli di tempo definiti durante il transito di un bolo di mezzo di contrasto attraverso
i vasi, le cavità o i tessuti in esame. Nella modalità flusso possono essere campionati fino ad otto tagli. Il
numero di campioni per taglio è selezionato in maniera tale che il totale dei tagli è pari a 80 o 160. Negli
studi di flusso cardiaco ciascun campione viene fatto scattare dal segnale elettrocardiografico cosicchè tutti
i campioni di un dato taglio sono ottenuti nella medesima fase del ciclo cardiaco. In particolare, il
campionamento è effettuato dopo ogni battito cardiaco in una fase corrispondente all’80% circa
dell’intervallo che segue l’onda R. Il mezzo di contrasto è generalmente iniettato come bolo endovenoso di
10-15 ml somministrato in 3-5 sec. I dati di flusso sono analizzati determinando la curva tempo-densità in
una regione d’interesse ed effettuando un adattamento numerico sulla risultante curva di flusso. Il parametro
di flusso più semplice da misurare è la gittata cardiaca. Questa misurazione è disponibile come prodotto
secondario di quasi ogni studio in modalità flusso. La gittata cardiaca si deduce misurando la curva tempo-
densità in una regione d’interesse all’interno di ciascuna cavità cardiaca o di ogni vaso di grosso calibro
quali l’aorta o l’arteria polmonare. Secondo l’equazione di Steward-Hamilton, la gittata cardiaca è data dal
rapporto tra la quantità di mezzo di contrasto iniettata nell’area e la curva tempo-densità. Nella modalità
cinematografica la capacità della TC ultraveloce di fornire dati in tempo reale è sfruttata per ottenere filmati
che mostrano le pulsazioni cardiache per l’individuazione di anomalie della motilità parietale, la
quantizzazione dei volumi cardiaci ecc. Allo scopo di quantificare la motilità parietale ventricolare, è
necessaria l’accurata estrazione del contorno che rappresenta la superficie endocardica ed epicardica.
Esistono diversi metodi per la determinazione dei contorni della parete miocardica. Il metodo più semplice
è quello di selezionare per questi un livello di densità e di trovare il contorno che corrisponde a questo
livello di densità. Il valore di densità può essere scelto al 50% dell’interfaccia sangue-tessuto o ad altri
valori che sono determinati sperimentalmente per dare dei risultatai corretti.

### 2.2.6 Risoluzione spaziale

La risoluzione spaziale e la risoluzione di densità contribuiscono a stabilire un limite dell’accuratezza con
la quale un contorno può essere definito, per esempio, per identificare il confine endocardico. I migliori
risultati si ottengono con una buona opacizzazione ventricolare, utilizzando 40 o più millilitri di mezzo di
contrasto. Poichè la risoluzione in densità è proporzionale alla dose somministrata al paziente, è preferibile
puntare a migliorare la risoluzione spaziale per migliorare l’accuratezza diagnostica. Infatti un aumento di
un fattore due nella risoluzione spaziale, permette una sensibile riduzione della quantità di mezzo di
contrasto da iniettare nel paziente.

## 2.3 Strumentazione

### 2.3.1 Il Tubo a Raggi X

Il Tubo a Raggi X (*Figura 2.5*) è un semplice tubo a diodo nel quale è fatto il vuoto; è formato da un catodo (composto
da un filamento riscaldato) che emette termicamente elettroni, e da un anodo che li attrae.

<img src="./images/fig_2_06_p45.png" alt="Figura pagina 45" style="width:100%;">

*Figura 2.5. Schema di un tubo a raggi X*

La tensione $V_F$ fa scorrere $I_F$ attraverso il filamento metallico, riscaldandolo per Effetto Joule. Il catodo
emette gli elettroni e, se $V_A$ è abbastanza alta, vengono attratti dall’anodo e formano una corrente nel vuoto
IB. $VA$ vale circa 100kV ed è tale da imporre agli elettroni una velocità elevata; circa l’ 1% degli elettroni
che raggiungono l’anodo collidono con atomi e producono Raggi X che a loro volta passano dal tubo allo
spazio esterno. Gli elettroni sono emessi dal catodo per agitazione termica che fornisce loro energia
sufficiente per sfuggire alla forza attrattiva del tubo a vuoto. Il valore di questa energia detta Funzione
Lavoro $E_W$ varia da metallo a metallo.
$I_B$ dovuta all’Agitazione Termica si ricava dalla Meccanica Quantistica e vale:

$$
I_B = C_O \, A_C \, T^2
\exp\left(-\frac{11600\,E_W}{T}\right)
$$

con: $A_C$ = area del catodo ($m^2$), $C_O$ = coefficiente proprio del materiale del catodo, $T$ = temperatura del
catodo (K).

Se $V_A$ non è abbastanza alta, intorno al catodo si formano nuvole di elettroni che, appena emessi, ricadono
su di esso. $I_B$ che è funzione della temperatura può essere controllata variando la tensione del filamento: in
questo modo si varia $I_B$ mantenendo $V_A$ costante $$
1980\,\mathrm{K} \leq T \leq 2400\,\mathrm{K}
\quad \Rightarrow \quad
0 \leq I_B \leq 110\,\mathrm{mA}
$$.

I Raggi X usati in medicina sono quelli generati dagli elettroni che collidono col nucleo (e non con gli
atomi), i quali vengono scatterati producendo uno Spettro di Radiazione X (Radiazione di Bremsstrahlung);
questa è causata dalla variazione di velocità del raggio di elettroni che riduce la sua energia cinetica di un
fattore pari all’energia del Raggio X.


<img src="./images/image_2_6.png" alt="Figura pagina 45" style="width:100%;">

*Figura 2.6. Schema del complesso tubo RX - rivelatore*

### 2.3.2 Funzionamento della TAC

Con il metodo tomografico, mettendo in movimento contrapposto la sorgente radiogena e il rivelatore, ed
usando appositi algoritmi, si può fornire una mappa dei coefficienti di assorbimento di una sezione
trasversale all'asse del corpo in esame, eliminando le tracce degli altri piani anatomici. Tale mappa viene
ricostruita a partire da una serie di (idealmente) infinite proiezioni radiografiche del corpo stesso, eseguite
per direzioni diverse, su un angolo di almeno 180 gradi.
Per eseguire la TAC il paziente viene posizionato tra la sorgente radiogena e il sistema di rivelazione in
un'apposita apertura circolare, in modo che il piano individuante lo strato da analizzare coincida con la
sezione mediana di detta apertura.
Lo spessore dello strato, dell'ordine di 3 - 10 mm, é determinato dallo stesso fascio di Raggi X.
Successivamente, il soggetto viene irradiato ed una serie di rivelatori rivela l’entità dei RX che lo
raggiungono, dopo avere attraversato il corpo. In questo modo, scandendo in sequenza strati del corpo del
soggetto, è possibile ricostruire l’intero corpo tramite le sue sezioni.
Nei sistemi di prima generazione il fascetto di Raggi X é a "pennello" e si usa un solo rivelatore (oppure
due rivelatori affiancati nella direzione normale allo strato, nel caso di analisi simultanea di due strati). Il
principio di acquisizione si basa su movimenti successivi di traslazione e di rotazione della sorgente
radiogena e del rivelatore, meccanicamente solidali. L'angolo di scansione é di 180 gradi e i passi angolari
sono di 1 o 2 gradi. L’operazione richiedeva un eccessivo tempo di scansione, dell'ordine di 3 minuti per
l'analisi di uno strato craniale, dell'ordine di 5 minuti per uno strato dell'addome o del torace.

<img src="./images/fig_2_08_p47.png" alt="Figura pagina 47" style="width:100%;">

*Figura 2.7. Schema del sistema di acquisizione con un emettitore e più rivelatori*

### 2.3.3 Struttura completa di una TAC

Le moderne apparecchiature TAC utilizzano lo Scanner rappresentato nello schema a blocchi di *Figura 2.8*.

<img src="./images/fig_2_07_p47.png" alt="Figura pagina 47" style="width:100%;">

*Figura 2.8. Schema di una TAC*

Le componenti principali di una apparecchiatura TAC sono le seguenti:

Il gantry è la struttura meccanica a cui sono rigidamente fissati il tubo radiogeno ed i detettori. Consente la
rotazione del sistema tubo-detettori durante la scansione e comprende il tunnel dentro il quale viene inserito
il paziente per l’esame.

Il tavolo portapaziente è il lettino su cui si distende il paziente per l’esame. Consente movimenti verticali
e longitudinali (velocità fino a 20 mm/s), di solito servoassistiti, per l’inserimento nel tunnel e per l’esatto
posizionamento.

Il complesso radiogeno è costituito da un tubo a Raggi X ad anodo rotante, con o senza griglia, ad emissione
pulsata o continua. L’alimentazione in continua ad alto voltaggio alimenta il tubo a Raggi X che può ruotare
meccanicamente lungo una circonferenza. I Raggi X attraversano il paziente che si trova all’interno di un
tubo al centro di questa circonferenza, ed arrivano a migliaia di rilevatori fissati lungo la circonferenza
stessa. Nei sistemi pulsati una singola emissione ha una durata dell’ordine di alcuni millisecondi e ad essa
corrisponde una vista dell’oggetto in esame. Sono richieste alta capacità di smaltimento del calore e stabilità
nell’intensità della radiazione.

Per i detettori esistono due tipologie costruttive.
La prima è basata su rivelatori a stato solido (soprattutto ioduro di cesio, CsI, e tungstato di cadmio) che
producono radiazione luminosa se irradiati a RX, combinati con fotomoltiplicatori o fotodiodi.
La seconda è basata su camere a ionizzazione con gas ad alta pressione (xenon). I rilevatori sono formati
da piccole camere di ionizzazione, piene di un gas tipo xenon ad alta pressione(dai 600 ai 2500 kPa, per
aumentare l’efficienza di rivelazione). I lati delle camere di ionizzazione sono sigillati e comprendono
ognuno un conduttore, in modo tale da formare un condensatore. Quando un Raggio X ( eventualmente
attenuato nell’attraversare il paziente ) entra nella camera e ionizza un atomo di xenon, lo fa migrare verso
la piastra del ricevitore e provoca quindi una corrente; questa è proporzionale alla radiazione ed il suo valore
è utilizzato dal computer come dato per ricostruire l’immagine. In alcuni modelli di TAC, il
fotomoltiplicatore è stato sostituito da un fotodiodo allo stato solido che consente la costruzione di un
complesso di rivelatori di dimensioni ridotte (detettori allo stato solido). In tali sistemi è possibile
modificare via software il guadagno dei fotodiodi. Le prestazioni dei due tipi di rivelatori sono globalmente
equivalenti, poiché i rivelatori a stato solido hanno un’efficienza maggiore di quelli a ionizzazione che però
possono esser realizzati con dimensioni minori, in modo da favorire un loro maggior compattamento.

I computer utilizzati sono in genere “general purpose”, con funzioni di comando e controllo di stato,
interfacciato ad uno o piu’ microprocessori dedicati all’acquisizione e visualizzazione dell’immagine. Un
microcomputer dedicato controlla la temporizzazione, la tensione dell’anodo e la corrente del fascio. Il
computer, nota la posizione del tubo , controlla l’uscita del rilevatore diametralmente opposto al tubo stesso;
dopo che il tubo ha compiuto un giro intero e la scansione è completa,il computer elabora i dati acquisiti e
fornisce in uscita un’immagine relativa alla sezione trasversale del paziente. La memoria di massa per la
conservazione delle immagini digitali è costituita da Hard Disk, memorie magnetiche, dischi ottici etc..

Nella **TAC convenzionale** per ogni scansione si ha la ricostruzione di una sola immagine e si chiede al
paziente un’assoluta immobilità, una sospensione del respiro, mentre il tubo ruota ed il lettino porta-
paziente rimane fermo. Poi, si invita il paziente ad un respiro libero, mentre il lettino porta-paziente si
sposta di un certo incremento ed il tubo Rx ritorna in posizione di partenza dopo aver ruotato per oltre 360°,
il computer elabora i dati acquisiti per restituirci, poi, un’immagine visibile sul monitor. Questa sequenza
viene ripetuta tante volte fino a coprire tutta la regione da esaminare.

E’ da far notare che durante lo spostamento del lettino non vi è alcuna emissione di Rx e, quindi, non si ha
nessuna acquisizione di immagini per tutto lo spessore di incremento con possibilità di perdere valide
informazioni diagnostiche su piccoli elementi. Inoltre, nelle successive scansioni, l’apnea del paziente è
certamente diversificata dalla precedente apnea con conseguente spostamento di elementi patologici più
cranialmente o caudalmente, con facile possibilità di non poter essere rilevato nelle scansioni. E’, quindi,
importante sottolineare come la TC convenzionale sia caratterizzata da una discontinuità spazio-temporale.
A partire dalle immagini degli strati successivi del corpo, è possibile, tramite opportuni algoritmi, ottenere
la ricostruzione 3D del corpo stesso e rappresentarla secondo varie “viste", come mostrato in *Figura 2.9*.

<img src="./images/fig_2_09_p49.png" alt="Figura pagina 49" style="width:100%;">

*Figura 2.9. Esempio di acquisizione di più sezioni.*

Nella **TAC a Spirale** il fascetto di Raggi X é a "ventaglio" con un'apertura da 40 a 50 gradi, che congloba
interamente l'oggetto in esame; il numero dei rivelatori é elevato, da 600 a 5000, disposti lungo una corona
circolare completa, in posizione fissa attorno all'oggetto. Solo la sorgente radiogena ruota all'interno della
corona dei rivelatori ed intorno al centro di questa, che corrisponde al centro del campo di misura.
Il gantry risulta così più leggero e semplificato, e per angoli di rotazione di 360 gradi si raggiungono tempi
minimi di scansione dell'ordine del secondo con possibilità, ovviamente, anche di acquisizioni con tempi
più lunghi.
Durante la rotazione della sorgente radiogena, un raggio del fascio X emergente va a colpire un rivelatore
ed esplora tutto il campo di misura, formando una proiezione conica.
Lo sviluppo di tale apparecchiatura è dovuta sia al computer che alle maggiori possibilità di resistenza dei
tubi a Raggi X, alle migliori qualità-efficienza dei detettori ed al nuovo sistema "slip-ring" (senza
l’utilizzazione di cavi) per l’alimentazione del tubo a Raggi X.
Con la tecnica a “slip ring”( contattori ad anello) si semplifica il sistema di cablaggio e connessione e si
evita la necessità di fermare il movimento dei rivelatori e/o del sistema di emissione alla fine di ogni
rotazione e di invertire il verso di rotazione, per non intrecciare i cavi. Questo sistema di connessione è
costituito da un insieme di contatti su cui corrono una serie di spazzole conduttive, in modo da non
richiedere il cambio di verso durante la rotazione continua.

E’ così possibile utilizzare la tecnica di scansione a spirale, in cui i rivelatori e/o il tubo a Raggi X ruotano
con continuità mentre il tavolo trasla (con velocità fino a 20 mm/s), introducendo il paziente nel gantry, e
sottoponendo così all’esame sempre nuove sezioni del corpo da cui vengono acquisiti i dati.

Il numero delle scansioni, max 35 circa, avvengono in un solo atto respiratorio (apnea inspiratoria o
espiratoria) e quindi l’organo o gli organi da esaminare sono fissi in una data posizione. Si acquisiscono
scansioni "volumetriche" in "modo spirale" contigue fra di loro, senza artefatti da movimento o da atti
respiratori diversificati.

<img src="./images/fig_2_10_p50.png" alt="Figura pagina 50" style="width:100%;">

*Figura 2.10. Scansione TAC a spirale*
