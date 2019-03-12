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
