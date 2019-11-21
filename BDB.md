% Biomedical Data Bases
% Saul Pierotti
% \today

# Introduction
* A database is an organized collection of data
* A DBMS is a piece of sofware that allows DB implementation and data mining
	* It allows data storing, retrieval, to perform backups, to maintain security
* Curation is a synonim of manual annotation
* In the last few years there has been a big effort to standardize DBs
* Even in the best DBs there are errors (!)
* Integration among DBs happens with corss-linking and with merging of DBs
	* Uniprot is an example
* Not all the structures available are on PDB (!)
	* Pharmaceutical companies have their own provate DBs
* Some DB terms
	* A record is a DB entry containing different fields
	* An accession key is a unique identifier of a record
	* A table is a DB file containing many records
		* Different tables can be connected by the same accession key for some records
	* A query is a data request submitted to a DB
* A query can be organized with boolean operator, in order to retrieve the desired result
* The schema of a DB is the logical structure of the data
	* A schema can be written in a flatfile, XML, ecc.
* The instance is the set of actual data
* The schema allows the interpretation of the instance
* Pubmed is based in Betsheda, at the National Library of Medicine
* Many DBs have built-in a way to retrieve data from the command line in a structured way
	* Entrex Direct allows to retrieve results from Entrez in the Unix command line
* The serch engine of PubMed uses automatic term mapping: if I do not specify the search filed, it tries to guess the correct one for each term in the query
* It first looks for the query in the MeSH Translation Table, then for the Journal translation table and then for an Author Index
* MeSH (Medical Subject Headings) is a list of common search terms that are classified in the correct context
	* If I search MeSH directly for a term, it gives me a list of possible meanings
	* Topics in MeSH are organized in a hierarchical wayH
	* I can limit my search to some topics
* Some of the main servers that we will use
	* NCBI (USA) hosts PubMed
	* SIB (Switzerland) hosts the tool ExPASy
		* In ExPASy, we can find SwissModel, UniProt, T-Coffee, LALIGN
		* T-Cofee is a really powerful alignment tool from Prof.Cedric Notredame, who maybe will give us an advanced lecture
	* EBI-EMBL (Germany and England)
		* It started in Heidelberg and then was transferred to Hinxton
		* They provide a lot of training schemes, and freely available data
		* Ensemble is a genome browser from EBI
		* It hosts also InterPro
* Elixir is an european platoform for bioinformatics data resources and tools
	* Casadio is on the board of directors of Elixir

# Uniprot
* Uniprot is composed of entries from Swiss-Prot, PIR and TrEMBL, and from external sources
	* PIR was founded but Margaret Dayhoff, the creator of PAM matrices and of the first protein sequence atlas
	* SwissProt was part of SIB and it is the most well-curated part
	* TrEMBL are automatic translations of EMBL DNA sequences
	* It became a central hub for protein information
	* It offers extensive cross-linking
* Uniprot is itself composed of different parts
	* The UniProt Archive (UniParc) is a comprehensive and non-redundant database that contains most of the publicly available protein sequences in the world. Proteins may exist in different source databases and in multiple copies in the same database. UniParc avoided such redundancy by storing each unique sequence only once and giving it a stable and unique identifier (UPI) making it possible to identify the same protein from different source databases. A UPI is never removed, changed or reassigned. UniParc contains only protein sequences. All other information about the protein must be retrieved from the source databases using the database cross-references. UniParc tracks sequence changes in the source databases and archives the history of all changes. UniParc has combined many databases into one at the sequence level and searching UniParc is equivalent to searching many databases simultaneously.
	* The UniProt Knowledgebase (UniProtKB) is the central hub for the collection of functional information on proteins, with accurate, consistent and rich annotation. In addition to capturing the core data mandatory for each UniProtKB entry (mainly, the amino acid sequence, protein name or description, taxonomic data and citation information), as much annotation information as possible is added. This includes widely accepted biological ontologies, classifications and cross-references, and clear indications of the quality of annotation in the form of evidence attribution of experimental and computational data.
	* The UniProt Reference Clusters (UniRef) provide clustered sets of sequences from the UniProt Knowledgebase (including isoforms) and selected UniParc records in order to obtain complete coverage of the sequence space at several resolutions while hiding redundant sequences (but not their descriptions) from view. Unlike in UniParc, sequence fragments are merged in UniRef: The UniRef100 database combines identical sequences and sub-fragments with 11 or more residues from any organism into a single UniRef entry, displaying the sequence of a representative protein, the accession numbers of all the merged entries and links to the corresponding UniProtKB and UniParc records.
* When we publish something using a database, we need to specify the release that we used (!)
* SwissProt is composed of proteins manually curated entries from TrEMBL
	* The first step of curation is to asses if there is evidence at the protein level
	* GO-terms (and other ontologies), references, isoforms, PTMs (post translational modifications), polimorphisms, crosslinks are added
	* If available, the structure of the protein is reported, modelled or experimental
	* The correct nomenclature is established and reported
* If different isoforms of the protein are identified, the curator searches for the reason of the difference and documents it
* Different isoforms can be due to alternative splicing, natural variations, alternative initiation sites, erroneous prediction, ecc.
* Gene ontology is a classification of a sequence in terms of biological process, molecular function and cellular component
* The TrEMBL part of UniProtKB is mainly redundant, while SwissProt is not-redundant
* How to recognize a SwissProt entry from a TrEMBL entry in Uniprot
	* The accession key for TrEMBL proteins is an alphanumeric string, and the entry name repeats the accession key
	* The accession key for SwissProt proteins is an alphanumeric string, and the entry name is not related to the accession key
	* In the result page, rewied proteins have a golden badge, non reviewed proteins have a blue badge
* In Uniprot we can customize the result list to show the information we need
* Entries in UniProt are huge (!)
* Each entry has an annotation score in 1 to 5
* Functional information is a bit sparse in the entry, it can be in many different fields
* There is also a comment field in the entry
* We did an exercise about how to do an advanced search on UniProt and download the result as an Excel file, that I cannot reproduce here
