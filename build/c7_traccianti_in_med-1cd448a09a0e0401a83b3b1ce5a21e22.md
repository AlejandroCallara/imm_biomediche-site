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
