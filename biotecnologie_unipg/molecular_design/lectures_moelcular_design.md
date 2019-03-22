% Appunti Molecular Design
% Saul Pierotti
% \today


# Lex.1
* Facciamo progettazione, non sintesi

## Modelli
* I modelli sono impiegati in ogni settore, ma alcuni campi impiegano modelli hard ed altri soft
* Un modello hard è il modello ab initio, che permette di ottenere una proprietà a partire da una configurazione
	+ Uso modelli diversi per proprietà diverse
	+ I risultati sono approssimazioni della realtà
		+ Va bene per sistemi semplici (piccole molecole)
		+ E' utile come previsione, o se non è possibile fare l'esperimento
	+ Usa dati solo calcolati
* Un modello soft è più accurato, ma necessita di poter ideare un esperimento adeguato
	+ Usa dati sperimentali
	+ Noi utilizzeremo modelli dal soft al semi-hard
Il  padre della chemioinformatica è Gasteiger
	+ E' un chimico organico che ha sempre lavorato al pc
	+ Ha fondato Molecular Networks
	+ Verrà a fine aprile (!)

## Cose importanti per il corso
* Descrivere lo spazio biochimico
* Conoscere DBs
* Metodi per analizzare i dati
* Relazione proprietà e struttura
* Algoritmi
* Intelligenza artificiale
	+ E' nata con l'informatica
* Modelliamo le interazioni, non la struttura

## Rappresentare un struttura molecolare
* Una cosa è conpresa se esiste un suo modello
* Il nome dei composti deve essere in base alla struttura, non all'origine

## Nomenclatura SMILES
* Trasformo la struttura in un grafo
	+ Rimuovo gli idrogeni
	+ Apro gli anelli ponendo un numero ad ogni rottura, che mi permette di identificare gli atomi separati
	+ Il cicloesano può essere scritto C1CCCCCC1
	+ Se un atomo chiude 2 anelli gli si assegnao 2 numeri consecutivi (es. C1CCCC2CCCCC12)
	+ Se voglio indicare più di 9 cicli premetto il simbolo % (l'atomo che chiude il cilo 12 è C%12)
* Indico i legami in modo standard
	+ Scrivo 2 atomi consecutivamente per un legame semplice (es. CC)
	+ In alcuni casi è necessario esplicitare il legame con - (es. 2 cicli aromatici collegati tra loro)
	+ = per doppi legami
	+ \# per triplo legame
	+ $ per quadruplo legame
	+ . per un legame non esistente (es. [Na+].[Cl-])
	+ : per un legame aromatico con parziale carattere di doppio legame
* I composti aromatici possono essere rappresentati in vari modi
	+ Con i doppi legami alternati (Kekulè) C1=CC=CC=C1
	+ Con il simbolo (:) C:1:C:C:C:C:C1
	+ Scrivendo i costituenti del ciclo in minuscolo c1ccccc1
* Le ramificazioni sono indicate con parentesi (es acido acetico CC(=O)O
* E' possibile indicare stereoisomeri
	+ Per l'isomeria cis-trans indico con F/C=C/F (oppure F\\C=C\\F) l'isomero trans e F/C=C\\F il cis (oppure F\\C=C/F)
	+ Gli stereoisomeri RS si indicano con @ se S e @@ se R (@ è una spirale antioraria!)
	+ Il senso è quello rispetto al primo atomo elencato del centro chirale
	+ L-Ala si indica N\[C@@H\](C)C(=O)O
* La codifica non è unica, una molecola può essere rappresentata in modi diversi
* Canonical SMILES è invece univoco
	+ Dipende da un algoritmo di canonicalizzazione
		+ E' un problema complesso

# Lex.2
* Le simulazioni di docking hanno una precisione sull'ordine degli Angstrom

## Dati chimici, farmaceutici e biologici

* I dati di struttura possono essere archiviati in vari formati
	+ pdb è tipico di macromolecole
	+ mol2 è usato per piccole molecole
* Tutti i formati riportano delle informazioni essenziali, e altre non essenziali
	+ Il tipo di atomo
	+ Le coordinate atomiche xyz
	+ Non è necessario inserire i legami, poichè sono dedotti dalle distanze atomiche
		+ In alcuni formati è comunque riportata una matrice di connettività
	+ Spesso sono riportate informazioni sulla confidenza della posizione
		+ La confidenza è assoluta per strutture calcolate e non sperimentali
	+ Può essere riportata la densità di carica elettronica dei vari atomi
		+ Viene salvata per evitare di ricalcolarla
	+ Può essere riportata la geometria molecolare, osssia lo stato di ibridazione

### Formato PDB
* Riporta il tipo di atomo, l'aminoacido, le coordinate
* La precisione è riportata tramite il B-factor
	+ La vibrazione termica causa incertezza nella misura
* ATOM indica tutti gli atomi che partecipano alla struttura di aminoacidi
* HETATM indica atomi di solvente, piccole molecole, ecc.
* Gli H non sono mai presenti perchè non visibili ai raggi X, ma possono essere inseriti su modelli virtuali

### Metodi sperimentali
* Tramite cristallografia ai raggi X, specie per macromolecole
* Per piccole molecole si usa più NMR
	+ Piu per ottenere la struttura, che la conformazione
	+ Oggi sono usati spettrometri NMR anche per le proteine, anche se non è sempre applicabile
	+ Non serve il cristallo (!)
* Per misurare precisamente gli H si usa la cristallogrfia a diffrazione neutronica

### Metodi teorici
* L'ab initio usa modelli hard basati esclusivamente su modelli quantistici, ossia risolve l'equazione di Schroedinger
	+ Non sempre è computazionalmente possibile
* I metodi semiempirici richiedono alcuni parametri sperimentali, e risolve la funzione d'onda solo per gli elettroni di valenza
	+ Sono più approssimati, ma più veloci
	+ Usano modelli di meccanica classica per gli altri elettroni
* Metodi di meccanica molecolare ignorano gli effetti quantisitici
* Inizio inserendo una struttura 2D al PC
	+ Utilizzando il metodo prescelto, viene calcolata la struttura 3D

### Cambridge Cristallographic Data Centre
* E' un DB a pagamento di strutture di piccole molecole
* Presenta molte più strutture di PDB

### Uso delle SMILES
* Posso usarle per effettuare una ricerca in DB, di solito per sottstrutture o gruppi funionali
	+ Questo permette di ricercare molecole con funzione biologica simile
	+ La SMILES che uso è detta query

## Calcolo delle strutture 3D
* Impiega metodi di minimizzazione energetica per calcolare la conformazione a partire dalla struttura 2D
	+ Minimizzano l'energia interna della molecola
	+ Il minimo di energia di solito corrisponde alla struttura cristallografica
* Si valuta come l'energia varia al variare della posizione, fino ad arrivare ad un minimo
* I metodi semiempirici e di meccanica molecolare sono troppo lenti
	+ Si parla di secondi, ma se i composti sono milioni è un problema
	+ E' stato inventato il metodo CONCORDE, che ha ridotto drasticament i tempi
	+ Con la potenza di calcolo attuale non è più un problema

# Lex.3
* La pKa è essenziale per determinare la permeabilità di molecole a livello delle membrane biologiche
* I farmaci tendono ad essere carichi a pH fisiologico
* Per convenzione si usa sempre la pKa, anche per le basi

## Cosa determina la pKa
* L'elemento a cui H+ è legato
	+ Più è elettronegativo meno è acido (?)
	+ Più è grande meno è aacido poichè distribuisce la carica (?)
* Effetto induttivo
	* Altri atomi elettronegativi presenti nella molecola influenzano l'acidità
	+ Mediato da legami $\sigma$
* Effetto di risonanza
	+ Mediato da legami $\pi$
* Ibridizzazione
	+ Più aaumenta il carattere s più l'acido è forte
* Effetto prossimtà
	+ Vicinanza di un gruppo che forma legami H intramolecolari

## Determinazione sperimentale della pKa
* Elettroforesi capillare, titolazione spettrofotometrica, titolazione potenziometrica
* Una pKa sperimentale è sempre preferibile ad una calcolata
* Non sempre è possibile la determinazione sperimentale per motivi tecnici o economici, e quando ho molte molecole

## Metodi per determinare la pKa
* I metodi ab initio sono troppo poco precisi e richiedono molto tempo
* I metodi sperimentali richiedono di avere a disposizione un campione
* La QSAR è la tecnica più usata

## A Perugia è stato sviluppato MoKa
* Molto veloce, accurato, considera le molecole poliprotiche
* Indipendente dalla rappresentazione esplicita degli H
* Calcola il LogP (partizione EtOH-H2O) e LogD (LogP in funzione del pH)
* Può essere allenato con un modello
* Si basa sui campi GRID, dove un probe si muove e valuta le interazioni con la molecola
	+ Si stanno ora sviluppando probes poliatomici
* Si creano dei livelli allontanandosi dall'atomo di riferimento
	+ Il livello 0 è l'atomo stesso, e si pongono tutti i bit a 0 eccetto quello per N
	+ La rappresentazione è non più binaria
	+ Si crea un fingerprint concatenaando questi bit
* Si crea una tabella che correla il fingerprint con la pKa, usata come modello di training
	+ Usa il metodo PLS 
* Bisogna considerare i tuatomeri, poichè ognuno ha una sua pKa (!)

# Lex.4

## Proteine
* Vi sono grandi investimenti sullo studio delle proteine
* L'utlizzo di enzimi permette di effettuare reazioni chimiche estremamente selettive
* I detersivi per lavatrice hanno una grossa componente enzimatica
	+ Le proteine sono stabilizzate con ponti SS e altri legami per farle resistere nelle condizioni di utilizzo
* Sono note almneno 500000 sequenze proteinche
* Le strutture proteiche 3D note sono molte meno

### Cristallografia
* E' importante avere un campione proteico puro
* E' difficile ottenere il cristallo
* Una volta era un processo artigianale, ora è automatizzato
	+ Si usano sali, acqua, metalli pesanti, tensioattivi
* Fare il cristallo serve ad amplificare il segnale (!)
	+ Più del 99% del raggio incidente non viene deviato
* Nella zona centrale dell'immagine ho il fascio diretto, mentre attorno il pattern di diffrazione
* Dal reticolo di diffrazione non ottengo la posizione ma la densità elettronica, non discerno bene atomi da gruppi di atomi
* Una volta bisognava fare fitting della sequenza sulla densità elettronica
	+ Ora si fa via software
* La strettezza della mappa di densità mi riflette la risoluzione della struttura che posso ottenere
* Si considera alta risoluzione 1.5$\AA$, bassa risoluzione 5$\AA$
	+ Per poterci lavorare bene deve essere almeno 2.5$\AA$

	+ Per poterci lavorare bene deve essere almeno 2.5$\AA$
* Oggi la cristallografia si fa in pochi centri specializzati
	+ In Europa si fa a Grenoble dove c'è un sincrotrone

## Trovare le binding pockets 
* Il primo step è trovare il sito o i siti di modulazione/legame
* Un singolo composto potrebbe interagire con più di una tasca nella stessa proteina
* E' possibile descrivere un pocketoma che raccolga le tasche note, e predica le interazioni di una molecola 
	+ E' rappresentato come network che misura la distanza di fitting di 2 tasche
* Si fanno simulazioni di fitting provando le varie tasche disponibili

# Lex.5

## Molecular interction fields (MIFs)
* Il prof ha scritto un libro che ci darà in pdf
* Goodford ha fondato la Wellcome Trust
* Il software **GRID** è gratis per l'accademia e a pagamento per i *for profit*
* Il target dei MIFs è l'insieme dell'interazione, non i singoli componenti
* La zona di interesse può essere l'intera molecola o una particolare porzione dello spazio
	+ La zona di interesse è definita con una griglia
* In tale regione metto un **probe** chimico, con cui la scansiono muovendolo per righe, colonne e piani
* La sonda chimica da utilizzare può essere scelta in base alle necessità
	+ Posso usare ioni, piccole molecole, ecc...
	+ Posso anche usare parti fittizie di molecole, ad esempio un gruppo OH non legato a nulla
	* La scelta della sonda dipende dal tipo di interazioni con la proteina che voglio studiare
* In ogni punto calcolo l'interazione del probe con la proteina
* Per simulare l'interazione calcolo la sommatoria dell'interazione del probe
	+ Valuto la Van der Waals, l'interazione di carica, i legami idrogeno ed il contributo entalpico
	+ Una risultante negativa indica attrazione, una positiva repulsione del probe
	+ L'interazione è valutata con tutta la proteina, anche nelle zone al di fuori dalla regione di interesse (!)
* La proteina ed il probe si muovono per minimizzare l'energia libera
	+ Oltre a legami diretti col probe, si valutano anche tutti i legami indotti all'interno della proteina stessa
	+ Questo può alterare la conformazione in zone distanti della proteina (!)
	+ Spesso una molecola d'acqua può fare da ponte per trasmettere un legame H

### Contributo di Van der Waals (Lendar-Jones (?))
* E' dovuto alla fluttuazione degli elettroni di valenza
* L'energia dell'interazione è 0 per distanze infinite, diviene negativa all'avvicinarsi dei nuclei, incontra un minimo e poi aumenta verso infinito per distanza 0
	+ A è il termine attrattivo e dipende da r^-6, B è il termine repulsivo e dipende da r^-12

### Contibuto Coulombiano
* L'interazione Coulombiana dipende da inversamente da r^2, direttamente dal prodotto delle cariche e dalla costante dielettrica del mezzo
* La costante dielettrica è un termine preponderante, in H2O l'interazione è 80 volte inferiore che nel vuoto
* In biologia si usa un'equazione modificata e più complessa
	+ Modella l'azione dell'acqua nelle proteine, in cui la costante dielettrica non è più costante (!)

### Contributo del legame H
* Il legame H è elettrostatico ma non è descritto adeguatamente dall'interazione Coulombiana
	+ La direzionalità modifica l'interazione al punto da doverla descrivere separatamente
	+ Dipende dalla geometria delle molecole interagenti e dei loro orbitali
* Ha una componente simile alla Lendar Jones (?), un contributo Coulombiano ed una componente geometrica
* Screenando DBs per la posizione di molecole d'acqua per un particolare gruppo chimico in diversi contesti trovo gli angoli di interazione più favorevoli
* Il carbonile forma legami H sopratutto in direzione dei lone pairs, ma un po' anche tra di essi
	+ Tra i lone pairs è possibile per H2O formare 2 legami con entrambi, ma la sovrapposizione orbitalica è inferiore
## Progettare una molecola
* Tramite vari probes vedo dove certi gruppi sono favoriti

# Lex.6

* Le interazioni deboli sono da 0 a 10 kcal/mol
	+ La Leidar-Jones è di circa 1 kcal/mol
	+ Il legame H è di circa 4 kcal/mol
	+ Le interazioni ioniche possono raggiungere i 15 kcal/mol
	+ La componente entropica è sulle 1.5 kcal/mol

## Componente entropica
* Posso utilizare un probe idrofobico, che spiazza delle molecole d'acqua di solvatazione da una superficie apolare
	+ Queste molecole d'acqua subiscono un guadagno energetico di circa 0.9 kcal/mol dovuto alle maggiori interazioni che possono formare quando non solvatano la superficie idrofobica
	+ Si ha un ulteriore guadagno per interazioni di Leidar-Jones di circa 1 kcal/mol tra la superficie ed il probe
* Consideriamo ora lo stesso probe idrofobico su una superficie polare
	+ Si hanno le stesse componenti di prima che determinano -1.9 kcal/mol, ossia guadagno entropico del solvente e interazioni Leidar-Jones
	* Si ha una perdita di energia dovuta alla rottura dell'interazione tra il gruppo polare e le molecole di acqua, di circa +2.5 kcal/mol
	* Il processo non è spontaneo in quanto ha un'energia di circa +0.6 kcal/mol
* Spesso è la parte più importante per il numero di interzioni che si formano
	+ Un farmaco idrofobico è spesso più potente di uno idrofilico perchè la sua interazione col target è favorita
	+ E' molto più tollerante ad imprecisioni nella previsione del legame, poichè è poco direzionale
* In biologia la selettività è data dalle interazioni polari, la potenza dell'interazione da quelle idrofobiche

## Piccole moelcole
* Interrogando la zona con +0.2 kcal/mol posso studiare la superficie della molecola
	+ Questo mi permette di calcolare il volume e l'ingombro sterico della molecola
* L'arginina è spesso usato come amminoacido idrofobico (!)
* Posso usare probes anfifilici per evidenziare dove avviene la transizione idrofobico-idrofilico
* Studiando con probe idrofobico, H2O e anfifilico il colesterolo posso predire come questo si posiziona sulle membrane
* Le strutture delocalizzate sono molto apolari poichè polarizzabili

# Lex.7

