# Capitolo 7: Traccianti in medicina

## Principi di cinetica dei traccianti

Il tracciante è un INDICATORE che segue, o traccia, una sostanza all’interno dell’organismo in esame. Le proprietà dei traccianti dovrebbero essere analoghe a quelle della sostanza in studio. Inoltre il tracciante dovrebbe essere introdotto nel sistema in quantità piccole tali da non perturbare il sistema stesso.

In uno studio con traccianti l’agente iniettato è la versione marcata (rintracciabile dall’esterno) della sostanza che entra nel processo in studio, che traccia quindi il destino di quella sostanza nella sua propagazione all’interno di un organo o tessuto. Nel caso di imaging funzionale, uno dei parametro di interesse è il flusso a livello dei capillari (noto anche con il nome di perfusione) e dal comportamento del tracciante si possono estrarre informazioni di perfusione.

La perfusione descrive il fenomeno del trasporto di nutrienti (glucosio, ossigeno) dal sangue arterioso al tessuto (*Figura 1a*), passando attraverso la barriera emato-tessutale (*Figura 1b*). Quantitativamente la perfusione è espressa come la quantità (o volume) di sangue arterioso che perfonde 1 gr di tessuto (o 1 ml) in un minuto. Le unità di misura sono: [ml (sangue)/g (tessuto)/minuto], oppure: [ml (sangue)/ml (tessuto)/minuto].

![alt text](./images/image.png)

*Figura 1.*

Il tracciante può essere:

- endogeno, quando sfrutta il meccanismo di contrasto tessutale che avviene con una certa metodica di imaging e quindi in base alle frequenze di impiego e al tipo di radiazione,

- esogeno, quando viene iniettato nel sistema circolatorio (mediante bolo o infusione continua). L’iniezione mediante bolo fornisce cinetiche transienti e l’equilibrio generalmente non viene raggiunto durante il tempo della misurazione. L’iniezione mediante bolo + infusione continua (B/I) permette di raggiungere l’equilibrio e fornisce misure di concentrazione del tracciante nel tessuto. In *Figura 2A* sono riportate le curve di ingresso al sistema circolatorio nei due casi, mentre in *Figura 2B* sono riportati esempi di curve misurate nel distretto anatomico. I traccianti esogeni possono essere suddivisi in:

- + diffusibili: sono in grado di diffondere in tutto il volume cerebrale (attraversano la barriera emato-tessutale)

- + intravascolari: rimangono all’interno dello spazio vascolare: per il cervello si tratta di ~ 4% del volume cerebrale

Uno studio di cinetica utilizza principi di cinetica per stimare parametri fisiologici di interesse dal comportamento cinetico del tracciante, permettendo uno studio quantitativo in vivo sia su animali che pazienti. In modo più generale si può definire la cinetica dei traccianti come la descrizione dinamica della concentrazione di un agente inviato al tessuto attraverso il sangue.

L’insieme delle teorie e metodologie che permettono di esaminare e descrivere la distribuzione del tracciante negli spazi anatomici partendo da misure di concentrazione, in relazione a funzioni fisiologiche e reazioni chimiche, si chiama ‘Teoria dei traccianti’.

![alt text](./images/image-1.png)

*Figura 2.*

In uno studio con i traccianti, i dati essenziali sono le curve di concentrazione nel tempo (*Figura 3*) dell’agente a livello di tessuto ($C_t$) e a livello di sangue arterioso ($C_a$). Tali curve sono chiamate curve concentrazione-tempo.

Quando lo studio viene effettuato mediante immagini, la funzione ($C_a$) viene misurata posizionando una ROI su una sequenza temporale di immagini (alternativamente può essere misurata mediante prelievo del sangue arterioso) in corrispondenza di un grosso vaso arterioso, mentre per la concentrazione tissutale ($C_t$) si posiziona una ROI sul tessuto sotto indagine.

Partendo dalle curve di concentrazione nel tempo, si utilizzano dei modelli matematici che mettono in relazione le grandezze misurate con i parametri funzionali.

![alt text](./images/image-2.png)

*Figura 3.*

Per comprendere intuitivamente la relazione tra parametri funzionali e misure, si supponga che la concentrazione $C_a$ nel distretto ematico sia mantenuta costante per un tempo lungo per poi tornare a zero (*Figura 4*).


![alt text](./images/image-3.png)

*Figura 4.*

In un intervallo temporale iniziale la concentrazione nel tessuto ($C_t$) crescerà in modo proporzionale al flusso ($f$) e quindi si potrà scrivere:


$$
\Delta C_t = f \cdot C_a \,\Delta t
$$


La relazione lineare tra flusso e concentrazione tessutale è lecita nell’ipotesi che nel tempo il tracciante non abbia ancora abbandonato il tessuto.

Quando il tracciante inizia ad abbandonare il tessuto attraverso il sistema venoso, l’aumento di concentrazione tessutale seguirà una legge di crescita non lineare regolata dalla differenza tra la quantità in entrata e quella in uscita verso il sistema venoso.

Il comportamento del tracciante può essere espresso in modo convolutivo ricorrendo alla definizione di funzione residua $r(t)$, rappresentata in *Figura 5*.

![alt text](./images/image-4.png)

*Figura 5.*

La funzione $r(t)$ descrive la probabilità che ha una molecola entrata nel tessuto al tempo $t = 0$ di trovarsi ancora nel tessuto al tempo $t$:

- $r(0) = 1$: le molecole del tracciante entrate nel tessuto al tempo $t = 0$ sono ancora all’interno del tessuto stesso

- $r(t_2- t_1)$: probabilità che una molecola di tracciante entrata nel tessuto al tempo $t_1$ sia ancora presente al tempo $t_2$.

- $r(\infty) = 0$

Assumendo un flusso costante (ipotesi di stazionarietà) durante l’esperimento, $r$ dipenderà dall’intervallo e non dal tempo $t$. Quindi la quantità di tracciante che entra nel tessuto tra $t'$ e $t' + dt'$ è: $f C_a(t')dt'$ e la probabilità che le stesse siano ancora nel tessuto al tempo $t$ è: $r(t-t')$.

Quindi la concentrazione nel tessuto al generico istante $t$ è data da: 

$$
C_t(t)
=
f \cdot C_a \otimes r(t)
$$

Si può quindi concludere che la relazione tra l’ingresso $C_a$ e l’uscita $C_t$ è di tipo convolutivo (*Figura 6*) e la risposta impulsiva del tessuto è proprio: $f r(t)$.

![alt text](./images/image-5.png)

*Figura 6.*


In *Figura 7* sono rappresentate funzioni tipiche per le quantità sopra definite.

![alt text](./images/image-6.png)

*Figura 7.*

Si può osservare come la ‘impulse function’ ottenuta come deconvoluzione tra $C_a$ e $C_t$ permetta di stimare il valore del flusso ($f$) all’istante $t = 0$, in cui $r(0) = 1$.


## Modellistica dei traccianti metabolici

## Introduzione

L’impiego di traccianti (isotopi radioattivi o stabili) nello studio di sistemi endocrino-metabolici è spesso una necessità. Esso costituisce praticamente l’unico modo per studiare la dinamica di un sistema in uno stato stazionario. Le attività sperimentali mirano a verificare le traiettorie ed il tempo impiegato dagli isotopi marcatori all’interno del corpo animale per raggiungere un sito finale o per venire eliminati dall’organismo. Il tracciato è la sostanza endogena (ad esempio il glucosio) che si vuole studiare e di cui abbiamo postulato un modello in forma compartimentale. Chiameremo invece tracciante una sostanza esogena che non è distinguibile dal tracciato da parte dell’organismo, ma che risulta tuttavia distinguibile in fase di misura. Il tracciante, essendo introdotto in piccolissime quantità, non perturba il sistema.

La tomografia a emissione di positroni (PET) ha reso possibile la rappresentazione visiva e la misura, in vivo, della concentrazione di traccianti radioattivi, emittenti positroni, a livello regionale (organi e tessuti). È uno strumento usato per valutare i processi molecolari in tutto il corpo.

La PET consente un'analisi qualitativa e quantitativa della concentrazione di tracciante radioattivo. L'informazione qualitativa, ottenuta mediante ispezione visiva, risulta più che sufficiente qualora si voglia avere informazione sulla localizzazione di difetti metabolici mentre risulta indispensabile estrarre un'informazione quantitativa qualora si voglia stimare, ad esempio, la velocità di utilizzazione del glucosio, il flusso ematico nel cervello, nel muscolo scheletrico e nel miocardio. Tale informazione si ottiene mediante l'uso di una modellistica appropriata.

Infatti si deve in generale ricorrere all'uso di modelli tutte le volte che sono necessarie quantificazioni di processi non direttamente misurabili poiché si verificano nella parte non accessibile del sistema ( ciò che può essere rilevato è il loro effetto sul pool accessibile, comunemente il plasma ). Alcuni di essi sono applicati per lo studio dello stato stazionario, altri per quello non stazionario del processo.

Si parla di stato stazionario quando il sistema si trova in uno stato di equilibrio dinamico in cui le masse e i flussi della sostanza in esame sono costanti nel tempo. In questo stato, la sola misura della concentrazione della sostanza in esame è di utilità limitata. La quantità di tale sostanza è infatti il risultato del bilancio dinamico (turnover ) di produzione e di utilizzazione e quindi due soggetti possono avere la stessa quantità di sostanza ma turnover diverso. Per misurare il turnover ed altri parametri del sistema è necessario generare dei dati dinamici con l'aiuto di un tracciante la cui concentrazione, non essendo esso prodotto endogenamente, riflette solo la cinetica del sistema. L'impiego di traccianti costituisce quindi l'unico modo per studiare la dinamica di un sistema in stato stazionario; permette inoltre, per quelli in stato non stazionario, di avere informazioni aggiuntive.

Più precisamente si indica con "tracciato" la sostanza endogena (ad esempio il glucosio ) che si vuole studiare e con "tracciante" una sostanza che viene somministrata dall' esterno nello stesso spazio fisico della sostanza naturale a cui si mescola uniformemente. Un tracciante ideale possiede le stesse caratteristiche fisiche della sostanza naturale, non ne altera il metabolismo, può essere misurato separatamente e non è prodotto dall' organismo. I traccianti contengono al loro interno un isotopo. Gli isotopi possono essere sia radioattivi che stabili; stabili sono quelli in cui il nucleo contiene un numero pressochè simile di protoni e neutroni mentre quelli radioattivi non godono di questa proprietà ed emettono particelle beta. Mentre la somministrazione di isotopi radioattivi implica dei rischi per i pazienti ( pur essendo somministrati in quantità ridotte ), gli isotopi stabili sono assolutamente innocui.

I traccianti possono essere somministrati con diverse modalità:

- bolo

- infusione continua

- infusione continua preceduta da bolo

ed infusi sia in vena che in arteria periferica. La velocità di infusione di un tracciante radioattivo si esprime abitualmente in [mCurie/min]. L'uso di un tracciante radioattivo non esclude ovviamente l'uso di un tracciante marcato con isotopi stabili in quanto le misure degli uni non influiscono con quelle degli altri e il loro uso contemporaneo permette inoltre la stima di parametri metabolici diversi.

Chiaramente il tracciante metabolizzato deve essere ritenuto nell’ organismo per tutta la durata dell'esperimento e la concentrazione del tracciante non metabolizzata che resta nel sangue e nei liquidi extracellulari deve essere trascurabile o in caso contrario valutata con precisione al momento delle misure. Questa condizione è più facilmente soddisfatta se i traccianti sono degli analoghi radioattivi .Poiché questi traccianti sono prigionieri in modo irreversibile nell’organismo studiato, si possono ritardare le misure PET fino al momento in cui la concentrazione del tracciante libero nel sangue e nel tessuto decade ad un livello insignificante. Quando i traccianti sono degli analoghi del glucosio, ci si deve limitare ad un ritardo da 30 minuti ad un’ ora per effettuare le misure. Quando i traccianti non sono degli analoghi ma dei veri substrati metabolici, una tale dilazione non è possibile perché le sostanze metaboliche marcate cominciano a lasciare il tessuto circa 5 minuti dopo la iniezione; il protocollo sperimentale deve dunque tenere conto esplicitamente del tracciante libero nel sangue e nel tessuto. Si soddisfa parzialmente questa condizione misurando il volume sanguigno locale nello stesso tempo in cui si misura il metabolismo regionale. Conoscendo il volume sanguigno locale si può calcolare la quantità di tracciante libera non solamente nel sangue ma anche nel tessuto stesso.

Un altro metodo che permette di valutare la concentrazione libera del tracciante nel sangue e nei tessuti consiste nel seguire l’uscita del tracciante metabolizzato al di fuori dell’ organo studiato e nel ripetere le misure del metabolismo più volte nei 5 minuti che seguono l’iniezione del tracciante. Il tasso di rinnovamento metabolico valutato con le misure successive decrescerà evidentemente in funzione del tempo. Si potrà valutare esattamente il tasso di rinnovamento metabolico in funzione del tasso di sparizione del tracciante. Un andamento tipico del tracciante nel tempo è illustrato nel seguente grafico:

![alt text](./images/image-7.png)

Con la PET, come già detto, è possibile misurare parametri di interesse fisiologico, più precisamente la misura:

- 15 del flusso per mezzo dell' ammoniaca marcata con azoto-13 o per mezzo di acqua marcata con ossigeno-

- dell'utilizzo di glucosio esogeno marcato con fluoro-18 -desossiglucosio

- del consumo di ossigeno nel ciclo di Krebs e misurato con l'acetato marcato con carbonio-11.

I principali modelli che si utilizzano con la PET sono:

- Modelli compartimentali (Sokoloff 1977)

- Modelli ingresso- uscita (Cunnigham 1993)

- Modelli a parametri distribuiti(Deussen et al. 1996 )

-  Modelli grafici(Patlak 1983)

Qui diamo un breve cenno ai due tipi di modelli che poi utilizzeremo per lo studio della velocità di metabolismo del glucosio.

## Modelli compartimentali

I modelli compartimentali hanno trovato un'ampia applicazione nello studio a livello di organo della cinetica dei traccianti PET. Essi forniscono una descrizione quantitativa su velocità di diffusione, trasporto e metabolizzazione di una determinata sostanza a partire dalla conoscenza della curva di attività tessutale e plasmatica del tracciante.

Un modello compartimentale consiste in un numero finito di compartimenti. Un compartimento è un insieme di materia che per l'organismo si comporta in maniera omogenea.

L'aggettivo omogeneo sta ad indicare sia:

- uniformità di informazione ossia due qualsiasi misure effettuate nel compartimento allo stesso istante danno lo stesso risultato.

- uguale probabilità da parte delle particelle di abbandonare il compartimento stesso.

Secondo il particolare modello, un compartimento può rappresentare un intero apparato, un organo, un tessuto , un insieme di cellule o una struttura chimica.

![alt text](./images/image-8.png)

Tali strutture sono connesse graficamente tra di loro mediante frecce orientate che indicano la direzionalità dei flussi di materia scambiata ed eventuali trasformazioni chimiche che avvengono nei siti presi in analisi: dove "Qi" indica la massa della sostanza del compartimento "$i$-esimo", le frecce uscenti denotano i flussi in uscita dal compartimento, in particolare $F_{ji}$ il flusso di materia diretto al compartimento $j$-esimo, $F_{oi}$ quello che abbandona irreversibilmente il sistema. Per quanto concerne i flussi entranti $F_{ij}$, $P_i$ e $U_i$ indicano rispettivamente:

-  il flusso proveniente dal compartimento $j$-esimo

-  il flusso endogeno (ossia appartenente al sistema in esame) che indica la sintesi de-novo della sostanza

-  il flusso di materia esogeno (ossia proveniente dall'esterno del sistema).

Il tratteggio indica che il compartimento è accessibile ossia possono essere effettuate misurazioni quantitative all'interno di esso di parametri e variabili. Per i sistemi endocrino-metabolici è solitamente possibile la misura di concentrazioni del tipo $C_i=Q_i/V_i$, dove $V_i$ è il volume del compartimento $i$-esimo. I modelli compartimentali sono costituiti da un numero finito di variabili del tempo legate tra loro da equazioni differenziali ordinarie che fanno riferimento a principi semplici e intuitivi quali quello di conservazione della massa. Infatti sfruttando tale principio è possibile scrivere per un sistema lineare e tempo invariante ad $n$ compartimenti il seguente set di $n$ equazioni differenziali ordinarie:

$$
\dot{Q}_i(t)
=
\sum_{\substack{j=1 \\ j\neq i}}^{n} F_{ij}(t)
-
\sum_{\substack{j=1 \\ j\neq i}}^{n} F_{ji}(t)
-
F_{0i}
+
P_i(t)
+
U_i(t),
\qquad
Q_i(0)=Q_{i0}
$$

dove $t$ rappresenta il tempo e $Q_{i0}$ la massa al tempo zero nel compartimento $i$-esimo; alcuni termini sono eventualmente nulli.

I flussi entranti $F_{ij}$ saranno proporzionali alla quantità $Q_j$ e ad un coefficiente $k_{ij}$ detto coefficiente frazionario di trasferimento dal compartimento $j$ a quello $i$. Una classe importante di modelli compartimentali è quella in cui le quantità $k_{ij}$ sono costanti. Le equazioni differenziali che le descrivono sono del tipo:

$$
\dot{Q}_i(t)
=
\sum_{j=1}^{n} k_{ij}Q_j(t)
-
\sum_{j=1}^{n} k_{ji}Q_i(t)
-
k_{0i}Q_i(t)
+
P_i\!\left[Q_1(t),Q_2(t),\ldots,Q_n(t)\right]
+
U_i(t)
$$

dove $i\neq j$.

Il precedente set può essere messo nella seguente forma compatta matrice-vettore:


$$
\dot{\mathbf{Q}}(t)
=
\mathbf{k}\mathbf{Q}(t)
+
\mathbf{P}\!\left[\mathbf{Q}(t)\right]
+
\mathbf{U}(t)
$$

$$
\mathbf{Q}(t)
=
\begin{bmatrix}
Q_1(t) &
Q_2(t) &
\cdots &
Q_n(t)
\end{bmatrix}^{T}
$$

dove:


$$
\mathbf{P}(t)
=
\begin{bmatrix}
P_1(t) &
P_2(t) &
\cdots &
P_n(t)
\end{bmatrix}^{T}
$$

$$
\mathbf{U}(t)
=
\begin{bmatrix}
U_1(t) &
U_2(t) &
\cdots &
U_n(t)
\end{bmatrix}^{T}
$$


con $K$ matrice quadrata $n$-dimensionale il cui generico elemento in riga $i$ e colonna $j$ è: $k_{ij}$.

Indicando con $m$ i compartimenti accessibili alla misura e con $M$ l'insieme dei loro $m$ indici $i$, le $n$ equazioni sono osservabili all' esterno tramite le $m$ equazioni di misura:

$$
C_i(t)
=
\frac{Q_i(t)}{V_i}
$$

con $i \neq M$

In forma matrice-vettore:

$$
\mathbf{C}(t)
=
\mathbf{H}\mathbf{Q}(t)
$$

dove $\mathbf{H}$ è una matrice $m \times n$ con tutti gli elementi nulli a parte gli elementi in colonna $i \neq M$ ed opportuna riga, che valgono $1/V_i$ ($V_i$ volume dell’$i$-esimo compartimento ). Poiché la matrice $K$ non è in genere nota, ovvero non si sanno dare dei valori numerici a tutti o a parte dei suoi elementi, si devono a tal scopo spesso utilizzare degli esperimenti con traccianti per ottenere gli elementi tramite tecniche di stima parametrica.

Nel caso in cui il sistema tracciato sia in stato stazionario si ha:

- $Q_i(t)=Q_i$

- $P_i(t)=P_i$

- $U_i(t)=0$ non essendovi ingressi esogeni

per cui valgono le equazioni:

$$
0
=
\sum_{j=1}^{n} k_{ij}Q_j(t)
-
\sum_{j=1}^{n} k_{ji}Q_i(t)
-
k_{0i}Q_i(t)
+
P_i
-
k_{0i}Q_i
$$

dove $i \neq j$ e $\mathbf{C}=\mathbf{HQ}$.

La dinamica del tracciante in questo caso è governata dalle equazioni:

$$
\dot{q}_i(t)
=
\sum_{j=1}^{n} k_{ij}q_j(t)
-
\sum_{j=1}^{n} k_{ji}q_i(t)
-
k_{0i}Q_i(t)
+
u_i(t)
$$

dove $i \neq j$ e il set dei [k_{ij}] è lo stesso delle equazioni precedenti.

In forma matrice-vettore le precedenti equazioni si possono scrivere nel seguente modo:

$$
\dot{q} = Kq + u
$$

Indicando con $m$ i compartimenti del tracciante accessibili alla misura e con $M$ l'insieme dei loro $m$ indici $i$, le $n$ equazioni sono osservabili all' esterno tramite le $m$ equazioni di misura che in forma matrice-vettore sono:

$$
\mathbf{c} = \mathbf{Wq}
$$

dove $\mathbf{W}$ è una matrice $m \times n$ con tutti gli elementi nulli a parte gli elementi in colonna $i \neq M$ ed opportuna riga pari alla quantità $1/V_i$.

Sotto queste condizioni la disponibilità di un tracciante permette quindi di utilizzare il vettore $\mathbf{c}$ per risalire ( essendo u noto ) tramite il procedimento di identificazione parametrica ai parametri $k_{ij}$, ai volumi $V_i$ e alla masse $Q_i$ dei compartimenti accessibili. Essendo noti i valori di $k_{ij}$ è possibile dall' equazione del tracciato trovare le variabili incognite e quindi avere una stima delle masse nei compartimenti non accessibili.

## Metodi grafici

L'obiettivo di tali metodi è quello di stimare parametri fisiologici di interesse a partire dall'analisi di una curva prodotta sul piano cartesiano utilizzando le curve dell'attività tessutale e plasmatica. Essi non permettono una completa quantificazione del processo fisiologico e danno solo informazioni su alcuni parametri.

Ad esempio nel caso dello studio con analogo PET del glucosio, tale metodo consente di stimare la velocità di utilizzazione del glucosio ma non i valori della velocità di trasporto e fosforilazione o la percentuale di volume vascolare presente nel tessuto stesso.

## Studio del metabolismo del glucosio

Lo studio è stato focalizzato sull'utilizzo della PET per quantificare la velocità di metabolismo del glucosio in organi quali il cervello, il muscolo ed il cuore (con particolare attenzione rivolta a quest'ultimo).

Il glucosio, come mostrato in figura, passa dal sangue alla cellula del tessuto e viceversa per via interstiziale.

All’interno della cellula il glucosio un po’ alla volta diviene, attraverso l’esochinasi, glucosio-6-fosfato, con un processo detto di fosforilazione. Come indice della velocità di metabolizzazione viene considerata la quantità del flusso di glucosio-6-fosfato che continua nel processo di metabolizzazione, che denomineremo Ri.

![alt text](./images/image-9.png)

*Schema del trasporto e del metabolismo di glucosio e di [18F]FDG.*


![alt text](./images/image-10.png)

*Il processo di fosforilazione del glucosio nella cellula.*

Il modello che prendiamo in considerazione non riguarda esattamente il glucosio, ma un suo analogo, il fluorodeossiglucosio marcato [18F]FDG, che, essendo radioattivo, può essere rivelato dagli scanner PET. Solitamente l'immissione di tale tracciante avviene per infusione continua preceduta da bolo che corrisponde a cento volte la dose che viene normalmente infusa in un minuto. L'infusione viene poi proseguita per centoventi minuti al termine dei quali si asssume che il glucosio tracciante sia in equilibrio con il glucosio endogeno presente in tutti i sistemi dell'organismo.

Il [18F]FDG essendo un analogo del glucosio e non un vero tracciante si comporta in maniera diversa dal glucosio naturale: il [18F]FDG fosforilato ([18F]FDG-6-P) non è, a differenza del glucosio naturale, un substrato per ulteriori reazioni metaboliche né della glicogeno sintesi né della glicolisi. In generale il vantaggio degli analoghi è che partecipano solo a un numero limitato di step in una sequenza di reazioni biologiche. È questo infatti il motivo per cui si sono sviluppati in biochimica e farmacologia: essi consentono di diminuire il numero delle variabili che devono essere misurate aumentando specificità e accuratezza della misura e di studiare in maniera selettiva uno step particolare di una sequenza biochimica. L’uso del [18F]FDG consente quindi una semplificazione del modello interpretativo del tracciante. Lo svantaggio è però che si devono usare dei fattori correttivi basati sul principio della cinetica competitiva di substrati o enzimi per tener conto delle differenze di comportamento tra il [18F]FDG e il glucosio naturale.

In altre parole:

[18F]FDG segue la cinetica del glucosio all'inizio del processo ed in seguito, sottoforma di [18F]FDG-6-P viene intrappolato nel tessuto non potendo essere ulteriormente metabolizzato.

Dunque tale comportamento permette di isolare la reazione di fosforilazione nella catena del metabolismo del glucosio in quanto la misura delle quantità 18F accumulata nel tempo, nel tessuto considerato, è in relazione con la velocità di fosforilazione del glucosio nel tessuto stesso.

## La costante LC

Come sempre quando si utilizzano degli analoghi è necessario introdurre una costante che tiene conto della diversa cinetica tra il glucosio e [18F]FDG (e cioè della diversità tra la velocità di trasporto e fosforilazione del glucosio e quella dell'FDG); tale costante è detta "Lumped Constant" LC.

A seconda che il [18F]FDG venga infuso in vena o in arteria in modo costante o che si effettui per iniezione di bolo vengono rispettivamente presentate per l'LC le seguenti formule:

$$
LC
=
\left(\frac{E^{*}}{E}\right)
\left(\frac{C_a^{*}}{C_a}\right)
\left(\frac{C_p}{C_p^{*}}\right)
$$

dove $(Ca^*/Ca)(Cp/Cp^*)$ che è circa uguale ad uno nell'uomo e nei ratti tiene conto della possibilità che il [18F]FDG e il glucosio possono distribuirsi in maniera non proporzionale tra il plasma e i globuli rossi.

$$
LC
=
\frac{
\displaystyle
\frac{
\int_{0}^{\infty} C_a^{*}(t)\,dt
-
\int_{0}^{\infty} C_v^{*}(t)\,dt
}{
\int_{0}^{\infty} C_a^{*}(t)\,dt
}
}{
\displaystyle
\frac{C_a-C_v}{C_a}
}
$$

nelle quali:

- il simbolo asteriscato indica il tracciante

- $C_a$ la concentrazione arteriosa

- $C_v$ quella venosa

- $C_p$ quella plasmatica

- $E=(C_a-C_v)/C_a$

Nel cervello è stato dimostrato che la LC è sostanzialmente stabile rispetto ad ampie variazioni della concentrazione plasmatica del glucosio nei soggetti non patologici.

Il suo valore tende comunque a diminuire progressivamente, anche se molto lentamente, nello stato iperglicemico, mentre in situazioni di ipoglicemia, ischemia o metabolismo accelerato il valore della LC può aumentare anche considerevolmente.

La LC può essere determinata con altri esperimenti, e se ne possono quindi trovare dei valori in letteratura.

Per il cervello vale la seguente tabella:

| Riferimento bibliografico | Soggetto | LC |
|---|---|---:|
| Reivich, 1985 | Uomini | 0.52 |
| Hasselbalch, 2001 | Uomini | 0.81 |

Il fatto che la LC sia costante e sia così definita risolve il problema della differenza di comportamento tra il glucosio e il suo analogo.


## Modelli del metabolismo del glucosio e [18F]FDG

Negli ultimi 20 anni sono stati proposti per la descrizione della cinetica del 18FDG vari modelli e metodi. Tra i più usati ricordiamo il modello compartimentale di Sokoloff (detto 3k perché caratterizzato da tre costanti di trasporto) che non prevede la defosforilazione del [18F]FDG, quello di Phelps (4k) che prevede invece la defosforilazione e quello di Schimdt (TH) che descrive l'eterogeneità tessutale, oltre al modello grafico di Patlak.

Il modello 3k

Tale modello si basa sulle seguenti assunzioni:

- il tessuto è omogeneo

- il glucosio è in stato stazionario per tutta la durata dell' esperimento

- i trasporti di [18F]FDG e [18F]FDG -6-P tra i compartimenti seguono cinetiche del primo ordine

- la concentrazione di [18F]FDG e di glucosio nell'arteria approssima la loro concentrazione capillare

- il [18F]FDG -6-P rimane, una volta formatosi, intrappolato nel tessuto per tutta la durata dell' esperimento.


![alt text](./images/image-11.png)

*modello grafico a tre compartimenti e 3k*

Sotto tali assunzioni le equazioni che descrivono la cinetica del [18F]FDG sono:

$$
C_m^{*}(0)=0
$$

$$
C_e^{*}(0)=0
$$

$$
\dot{C}_m^{*}(t)
=
K_3^{*}C_e^{*}(t)
$$

$$
\dot{C}_e^{*}(t)
=
K_1^{*}C_p^{*}(t)
-
\left(K_2^{*}+K_3^{*}\right)C_e^{*}(t)
$$

dove $C_p^*$ rappresenta la concentrazione plasmatica del [18F]FDG, $C_e^*$ la concentrazione tessutale del [18F]FDG, $C_m^*$ la concentrazione tessutale del [18F]FDG -6-P. Risolvendo il sistema di equazioni differenziali lineari a coefficienti costanti si ottengono i seguenti andamenti temporali:


$$
C_m^{*}(t)
=
\frac{K_1K_3}{K_2+K_3}
\left[
\int_{0}^{t} C_p^{*}(\tau)\,d\tau
-
e^{-(K_2+K_3)t}
\int_{0}^{t}
C_p^{*}(\tau)e^{(K_2+K_3)\tau}
\,d\tau
\right]
$$

$$
C_e^{*}(t)
=
K_1 e^{-(K_2+K_3)t}
\int_{0}^{t}
C_p^{*}(\tau)e^{(K_2+K_3)\tau}
\,d\tau
$$

L' equazione di misura nel cervello è:

$$
C_i^{*}(t)
=
\left(1-F_{bt}\right)
\left(
C_e^{*}(t)+C_m^{*}(t)
\right)
+
F_{bt}C_b^{*}(t)
$$

mentre nel cuore:

$$
C_i^{*}(t)
=
C_e^{*}(t)
+
C_m^{*}(t)
+
F_{bt}C_b^{*}(t)
$$

dove $C_i^*$ è la concentrazione di 18F all' interno della regione tessutale esaminata e $C_b^*$ è la concentrazione nel sangue intero. $F_{bt}$ è un termine necessario per tenere conto, nel cervello e nel muscolo, della presenza del volume vascolare all'interno della regione di interesse e nel cuore per correggere le misure tessutali dalla presenza del volume vascolare e dall' effetto dello spillover da plasma a tessuto che, a causa dell' alta radioattività plasmatica nel ventricolo sinistro, innalza artificialmente la radioattività tessutale. Campionando questa equazione agli istanti di tempo in corrispondenza dei quali si hanno i dati di misura tissutale si ottiene un sistema non lineare di equazioni da cui si ricavano i valori incogniti di $K_1$, $K_2$ ,$K_3$, $F_{bt}$.

Noti i parametri del modello [18F]FDG si riesce a stimare quindi la velocità di utilizzo ( fractional uptake) del glucosio Ri attraverso la seguente formula:

$$
R_i
=
\frac{K_1K_3}{K_2+K_3}
\frac{C_p}{LC}
$$

dove $C_p$ è la concentrazione plasmatica di glucosio (mg/dl) ed LC è la Lumped Constant.

### Il modello 4k

Nel 1979, da parte di Phelps e collaboratori, venne introdotta una variante del modello 3k che tenesse in considerazione la velocità di defosforilazione del 18-FDG-6-P, riscontrata in alcune prove sperimentali sul tessuto cerebrale.

![alt text](./images/image-12.png)

Tale modello presenta sempre tre compartimenti ma quattro costanti di velocità, come è illustrato nella seguente figura:

Le equazioni che lo regolano sono:

$$
C_e^{*}(0)=0,
\qquad
C_m^{*}(0)=0
$$

$$
\dot{C}_e^{*}(t)
=
K_1 C_p^{*}(t)
-
\left(K_2+K_3\right)C_e^{*}(t)
+
K_4 C_m^{*}(t)
$$

$$
\dot{C}_m^{*}(t)
=
K_3^{*}C_e^{*}(t)
-
K_4^{*}C_m^{*}(t)
$$

Le ipotesi alla base di questo modello sono le stesse fatte per in modello 3k con l’unica differenza che ora non si considera più il tracciante intrappolato nel tessuto per tutta la durata dell’esperimento. La velocità di utilizzo (fractional uptake) del glucosio da parte del tessuto anche in questo modello è
espressa dalla formula:

$$
R_i
=
\frac{K_1K_3}{K_2+K_3}
\frac{C_p}{LC}
$$

## Il metodo grafico di Patlak

![alt text](./images/image-13.png)

Anche con il metodo di Patlak, che è un metodo grafico, si giunge ad una stima della velocità di utilizzazione del glucosio partendo però dalla descrizione del processo di scambio di un tracciante tra sangue e tessuto tramite un modello compartimentale per il quale non si fa alcuna specifica assunzione nè sul numero di compartimenti nè sul tipo di collegamento tra di loro.

Si rappresentano su un piano cartesiano i punti di coordinate:

$$
y
=
\frac{C_i^{*}(t)}
{C_p^{*}(t)}
$$

$$
x
=
\frac{
\displaystyle\int_{0}^{t} C_p^{*}(\tau)\,d\tau
}{
C_p^{*}(t)
}
$$

dove $C_p^*$ è la concentrazione plasmatica di tracciante e $C_i^*$ è la concentrazione tessutale di tracciante.

Sotto l'ipotesi che esista un tempo t* a partire dal quale la regione tessutale che scambia in modo reversibile con il plasma risulti in stato stazionario con il plasma stesso, allora si ha che se per $t>t^*$ la curva rappresentata sul piano cartesiano:

- è una retta con pendenza $m$, esiste una regione irreversibile che non scambia materiale con nessun altro compartimento

- è una retta parallela all' asse delle ascisse, non c'e alcuna regione irreversibile ma solo regioni completamente reversibili

- è una curva concava, allora la regione non è completamente irreversibile ed esiste una piccola perdita di prodotto dalla regione irreversibile al plasma.

Il metodo non richiede nessuna assunzione sul tipo di tessuto ed è quindi applicabile sia in presenza di regioni tessutali omogenee che eterogenee.

Se utilizzando il metodo di Patlak si ottiene, nel caso del [18F]FDG, una retta con pendenza $m$ il valore di uptake del glucosio è dato da:

$$
R_i
=
m\,\frac{C_p}{LC}
$$

Nel caso invece in cui la curva sia concava ,il calcolo di $R_i$ risulta molto più complicato in quanto cade l’ipotesi $K_4=0$.

La limitazione maggiore di questo metodo consiste nella individuazione esatta del tempo $t^*$ a partire dal quale tutti i pool tissutali reversibili possono essere considerati in equilibrio con il plasma e nell’inutilizzabilità di esso qualora il tempo $t^*$ ecceda il limite pratico sperimentale.

Una scelta erronea di $t^*$ (che varia con il tipo di sostanza e di regione tissutale) implica una interpretazione non corretta dei risultati: si potrebbe classificare uno stato di non equilibrio tra plasma e tessuto come una perdita di prodotto dal compartimento irreversibile.

Infine, va osservato come il metodo di Patlak non permette di stimare parametri fisiologicamente interessanti quali, ad esempio, la velocità di scambio sangue-tessuto.

### Esempio: dati PET cardiaci

Il metodo descritto viene qui applicato per studiare la velocità di metabolismo del glucosio nel cuore in due pazienti.

Sono considerati i dati sperimentali ottenuti tramite misure PET riguardanti, nel primo caso, la concentrazione di tracciante [18F]FDG nel ventricolo sinistro, nella parete laterale e nel setto della ROI cardiaca mentre, nel secondo caso, la concentrazione di tracciante nel ventricolo, nella parete anteriore e nel setto sempre della regione di interesse.

I dati sono stati preventivamente corretti da eventuali errori di misura quali quelli introdotti dallo spillover (sovrastima della quantità di tracciante nella ROI dovuta all’influenza delle zone limitrofe).

I seguenti grafici mostrano gli andamenti temporali:

#### I CASO:

![alt text](./images/image-14.png)

#### II CASO:

![alt text](./images/image-15.png)

Le seguenti figure mostrano i risultanti grafici di Patlak, rispettivamente nel I e nel II caso:

![alt text](./images/image-16.png)

![alt text](./images/image-17.png)

Le rette tratteggiate di regressione sono quelle che meglio approssimano il tratto lineare delle curve di Patlak ed i valori numerici delle loro pendenze sono:

CASO 1:

$$
m_{\text{laterale}}
=
6.50\times10^{-4}\,\mathrm{s}^{-1}
$$

$$
m_{\text{setto}}
=
7.18\times10^{-4}\,\mathrm{s}^{-1}
$$

CASO 2:

$$
m_{\text{laterale}}
=
2.32\times10^{-4}\,\mathrm{s}^{-1}
$$

$$
m_{\text{anteriore}}
=
1.94\times10^{-4}\,\mathrm{s}^{-1}
$$


Ponendo $LC=0.67$, la concentrazione plasmatica di glucosio $C_p$ pari a $100 mg/dl$, la densità del tessuto cardiaco $d$ pari a $1.08 g/cc$ si ottengono i seguenti valori di velocità di utilizzo (fractional uptake) del glucosio da parte del tessuto:

CASO 1 :

$$
R_{\text{laterale}}
=
0.0540\,
\mathrm{\frac{mg}{g\cdot min}}
$$

$$
R_{\text{setto}}
=
0.0596\,
\mathrm{\frac{mg}{g\cdot min}}
$$

CASO 2 :

$$
R_{\text{laterale}}
=
0.0193\,
\mathrm{\frac{mg}{g\cdot min}}
$$

$$
R_{\text{anteriore}}
=
0.0162\,
\mathrm{\frac{mg}{g\cdot min}}
$$

## Traccianti per imaging molecolare

### Introduzione

Con il termine ‘Imaging molecolare’ si intende identificare una nuova area di ricerca che, combinando lo studio dei processi biologici alla base delle malattie, la tecnologia di imaging e i farmaci molecolari, ha come obiettivo il monitoraggio dei meccanismi molecolari specifici di patologie (tumorali, neurodegenerative), al fine di potenziare gli attuali strumenti di diagnosi, prevenzione e terapia.

Le attuali tecnologie per immagini sono legate essenzialmente alla visualizzazione di modificazioni macroscopiche non specifiche, fisiche, fisiologiche, metaboliche, che differenziano il tessuto patologico da quello normale, piuttosto che identificare gli eventi (cioè l'espressione genetica) responsabili della malattia. Questo cambiamento da un approccio non specifico ad uno specifico rappresenta un salto diagnostico importante e significativo (vedi Figura sotto), il cui impatto potrà fornire il potenziale per un precoce rilievo e caratterizzazione della malattia ed una valutazione del trattamento terapeutico.

![alt text](./images/image-18.png)


L'imaging molecolare ha le sue radici nella medicina nucleare, utilizzando adeguati traccianti radioattivi in relazione alle tecnologie di immagini impiegate, quali la PET e la SPECT. Ma anche altre tecnologie sono impiegate, quali ad esempio la microscopia a fluorescenza, gli ultrasuoni con l'utilizzo di opportuni mezzi di contrasto, la tomografia computerizzata, la risonanza magnetica.

![alt text](./images/image-19.png)


### Imaging molecolare con nanoparticelle

In medicina molecolare, con il termine tracciante si intende un veicolo di trasporto per imaging e trattamento farmacologico molecolare (*Figura sotto*).

![alt text](./images/image-20.png)

In particolare:
- 1) una sostanza che generi il contrasto e quindi visibile mediante la tecnica di imaging impiegata per effettuare la misura (es. radionuclidi, microbolle, gadolinio);

- 2) un mezzo di trasporto, adatto ad interstiziale, membrana cellulare) per raggiungere il bersaglio d’interesse. Può essere una piccola molecola, oppure una nanoparticella creata artificialmente. ad a attraversare le barriere biologiche (vascolare,

- Il materiale utilizzato come mezzo di trasporto può coincidere con la sostanza che genera il contrasto e quindi la visualizzazione, come nel caso delle microbolle o i liposomi per la tecnica ecografica e il perfluorocarbonio per la risonanza magnetica;

- 3) un sistema di targeting, per esempio una molecola che sia in grado di riconoscere un bersaglio e di legarsi ad esso (es. anticorpo monoclonale);

- 4) un farmaco da trasportare sul tessuto bersaglio;

- 5) un tessuto bersaglio, individuato in una proteina (targeting di proteine) o in un reporter gene (targeting genetico)

#### Meccanismi di accumulo nel tessuto

![alt text](./images/image-21.png)

EPR = enhanced permeability and retention

#### Esempi

##### Imaging ultrasonico
![alt text](./images/image-22.png)

##### Imaging MR

![alt text](./images/image-23.png)
