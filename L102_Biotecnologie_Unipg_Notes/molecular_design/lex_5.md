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
* E' dovuto alla fluttuazione degli elettroni di valenza*
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
