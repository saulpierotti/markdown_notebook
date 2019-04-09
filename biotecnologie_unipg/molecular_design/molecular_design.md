% Molecular Design
% Saul Pierotti
% \today

# Cosa studieremo
+ Progettazione di molecole, non sintesi
+ Come descrivere lo spazio biochimico
+ I DBs utilizzati nella progettazione molecolare
+ I metodi utilizzati per analizzare dati biochimici
+ La relazione tra proprietà e struttura delle molecole
+ Algoritmi sottostanti ai sistemi di previsione delle interazioni

# Uso di modelli nelle scienze sperimentali
+ I modelli sono impiegati in ogni settore scientifico, ma alcuni campi impiegano modelli hard ed altri soft
+ Un esempio di modello hard è il modello ab initio, che permette di ottenere una proprietà del sistema in esame a partire da una sua configurazione
	+ Uso modelli diversi per studiare proprietà diverse
+ I risultati ottenuti tramite modelli hard sono approssimazioni della realtà
	+ Le approssimazioni effettuate possono essere accettabili nella previsione di sistemi semplici (piccole molecole)
	+ Questi modelli sono utili come previsione, o se non è possibile effettuare l'esperimento reale
	+ Un modello hard usa dati solo calcolati
+ Un modello soft è più accurato, ma necessita di poter ideare un esperimento adeguato in quanto necessita di dati sperimentali
+ In questo corso utilizzeremo modelli che vanno dal soft al semi-hard
+ La chemioinformatica, scienza che applica modelli informatici a sistemi molecolari, è stata fodata da Gasteiger, un chimico organico
	+ Pur essendo un chimico organico ha sempre lavorato al pc e non ha mai fatto sintesi in laboratorio
	+ Ha fondato la company Molecular Networks
	+ Probabilmente verrà a fare una lezione a Perugia a fine aprile (!)
+ In questo campo sono molto usati modelli basati sull'intelligenza artificiale
	+ L'AI è una tecnica nata con l'informatica stessa
+ In chemioinformatica sfruttiamo modelli per predire le interazioni tra molecole, non la loro struttura
+ Una cosa si può definire compresa, conosciuta, se ne esiste un modello sufficientemente accurato
---
# Descrivere sinteticamente una molecola
+ Il nome di un composto è più utile che venga definito in base alla sua struttura, non alla suaa sua origine
+ La nomenclatura IUPAC...

## Nomenclatira SMILES
+ Trasformo la struttura in un grafo
	+ Rimuovo gli idrogeni
	+ Apro gli anelli ponendo un numero ad ogni rottura, che mi permette di identificare gli atomi separati
	+ Il cicloesano può essere scritto C1CCCCCC1
	+ Se un atomo chiude 2 anelli gli si assegnao 2 numeri consecutivi (es. C1CCCC2CCCCC12)
	+ Se voglio indicare più di 9 cicli premetto il simbolo % (l'atomo che chiude il cilo 12 è C%12)
+ Indico i legami in modo standard
	+ Scrivo 2 atomi consecutivamente per un legame semplice (es. CC)
	+ In alcuni casi è necessario esplicitare il legame con - (es. 2 cicli aromatici collegati tra loro)
	+ = per doppi legami
	+ \# per triplo legame
	+ \$ per quadruplo legame
	+ . per un legame non esistente (es. [Na+].[Cl-])
	+ : per un legame aromatico con parziale carattere di doppio legame
+ I composti aromatici possono essere rappresentati in vari modi
	+ Con i doppi legami alternati (Kekulè) C1=CC=CC=C1
	+ Con il simbolo (:) C:1:C:C:C:C:C1
	+ Scrivendo i costituenti del ciclo in minuscolo c1ccccc1
+ Le ramificazioni sono indicate con parentesi (es acido acetico CC(=O)O
+ E' possibile indicare stereoisomeri
	+ Per l'isomeria cis-trans indico con F/C=C/F (oppure F\\C=C\\F) l'isomero trans e F/C=C\\F il cis (oppure F\\C=C/F)
	+ Gli stereoisomeri RS si indicano con @ se S e @@ se R (@ è una spirale antioraria!)
	+ Il senso è quello rispetto al primo atomo elencato del centro chirale
	+ L-Ala si indica N\[C@@H\](C)C(=O)O
+ La codifica non è unica, una molecola può essere rappresentata in modi diversi
+ Canonical SMILES è invece univoco
	+ Dipende da un algoritmo di canonicalizzazione
		+ E' un problema complesso
