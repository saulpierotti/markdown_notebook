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
	+ Mediato da legami \sigma
* Effetto di risonanza
	+ Mediato da legami \pi
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
