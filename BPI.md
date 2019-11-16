% Bioanalytical Proteomics and Interactomics
% Saul Pierotti
% \today

# Introduction
* Most proteomic studies are based on mass spectrometry
* The program will be finished in December, in January we will only do exercises
* The examination is composed in a poster presentation and an oral part
	* A poster is a self-sufficient work
	* Usually it is prepared at the begininning of a scientist's career
	* We should base our poster on selected papers
	* The poster is not mandatory, but if we do it we will only be asked 1 question in the exam
* Proteomics is one of the main omics, but also interactomics and secretomics are becaming really interesting
* The data produced by omics are on the order of zetta and yottabytes
* Personalized medicine is important, and now we have the tools to implement it
* Proteomics can be structural, functional and differential (expression)
* Three main approaches: top-down, bottom-up and shotgun
* Many funding sources now require researchers to share raw data
* In silico-cloning: we need to know at least one software
* Other useful softwares are Pymol, Graphpad Prism, ImageJ
	* Graphpad Prism is a spreadsheet used to elaborate data and do statistics
* Proteomics is the large scale study of proteins, the proteome is the total amount of proteins coded in the genome
* Proteomics involves a spatial and temporal dimension, while the genome is static
	* It is really noisy (!)
	* Proteins are really diverse, and their processing is complex
	* They are present in a really broad concentration range
	* There is no PCR for proteins (!)
* Unnatural amino acids are really interesting, and there are many patens about them
	* They are used frequently in cosmetics (!)
* Proteases are everywhere (!)
* Aromatic amino acid tend to be in $\beta$ conformations
* MALEK tend to be in $\alpha$ helices
* 1/3 of drugs target GPCR receptors
* Membrane proteins are hard to study
* An antibody is around 150 kDa, it is a big protein
* Is of huge clinical interest to find fluorescent proteins that emit in the red spectrum
	* Most tissues absorb really well green light, and red is the least absorbed part of the spectrum
* Mutagenesis can be performed rationally or randomly
	* Random mutagenesis is made with kits that make an imprecise PCR
	* We can substitute any possible aminoacid in a specific postion that we know to be important
* The top-down aprroach starts from the protein
* The bottom-up approach uses peptides deriving form digestion of the protein
* The shotgun approach uses different peptides deriving from many proteins
* The less complex the protein mixture, the better (!)
* Proteins can be separed with different chromatographies or electrophoresis, microdialysis
* We can use depletion techniques to remove typical high-abbundance proteins
	* There are kits to remove albumin with spin columns
* Protein electrophoresis can be done in native conformation or by SDS-PAGE
* Immunological techniques are Western blot, ELISA, immunoprecipitation
	* Antibodies have affinity constants ranging from $10^9$ to $10^12$ M
* The upper limit for the number of resolvable proteins in a 2D-PAGE is 10000
* Spot identification in 2D-PAGE can be done by MS or by image analysis
	* Image analysis can be done by comparing our image with gel images of identified proteins present in databases
	* I usually work on master images created by combining 5-10 images of gels run in the same condition, to reduce noise
* Differential PAGE (DIGE) runs 2 samples on the same gel, with different labels, so to be able to compare expression differences between them

#Ila notes
SMART is a tool by providing the primary structure it predicts the 3 or $4^{tenary}$ structure.

##Tools of Proteomics
We need to avoid the formation of aggregates and dimers.

During the extraction process we need to avoid chemical or enzymatic reactions that may later or destroy the protein.

Keratins 

Contaminants - most common ones nucleic acids!!!
Nucleases may get rid of those.

There are several proplems with the robustnes of results. MS analysis is very standardized - but the **preparation** is the key. Outcomes may be very different depending on the preparation.

Cell disruption methods...

Sample preaparation
Protains must be *denatured* and soluble. 
- urea
- thiols (reduces disulfid bonds) DTT (dithiotreitol)
- detergents 
- protease inhibitors

$H_2_N$ 

Rule of thumb:
increasing DTT (dithiotreitol) will increase the number of visible spots (p34 slides)

###2D Gel Electrophoresis
2 orthogonal sepparations of the sample
 $1^{st}$  **dimension** according to the Ip
- iso electric focusing: pH gradient is created by imobilized chemicals. The pH range can be narrowed down according to the protein under investigation. That way the resolution may be increased.
5000V - after 10hrs it will be done -> main limitation is the time it requires... 
After the migration the disylfide bonds may be reduces. 

**2^nd dimension** according to the weight of the molecule

In *ideal conditions* we may identify up to 2000 proteins in each run.

Senitivity and suitability are the factors you need to consider when choosing a method.

**mastergel**
average of different samples
is a sort of µ 
minimum number is 

Picture: Detection/matching
What information can be retrieved
If the protein has a different isoform- it may have a different structure - so it could be in a different spot in the picture.

**gels are NOT quatitative**

Master gels may avoid 

**Gelimage warping**
readjusting the migration of protein coordinates ?????

Geldatabases may help identifying the blobs even if you cant use mass spectrometry to identify yours.

This search may only return you a range of iPs and weight of molecule.
These pictures are interactive - you may clic on the coordinates, to retrieve information. 

If you are studying liver tumors and you wat to identify a new biomarker. So you only know the tissue - but the target is unknown. So on the swiss 2D Page the organism may be chosen from a drop down menu. 

Peptide masses from trypsin digestion? Well talk about that later.

**Differential analysis**
Normal vs Pathologic
Master gels with a minimum of 50 healthy and 50 pathological cases.

**Limitations**
Scarce reproducibility.
For clinical samples 5-10 is the rule to obtain reprocubility.
Comigration is a problem. Instead of having discreted spots you have a biq smear "streaking" or "comigration"

Weak spots may present on a background that is not very distinguished.

**increasing resulution**
by changing the experimental conditions. By decreasing the pH range but ONLY if you know the iP of your protein.

There is a trend to avoid 2D at all 

Sorry it was very hard for me today a lot of holes.

She will put out slides for us to read about the background. The title is “not for the exam” =)
the only approved way of doing drug and doping tests is with MS

M/C ratio
Single charged ion.

With maldi we have mostly single charged ions.
For bigger molecules we have multiple charges. The gaussian distribution shows different charges.

With bigger molecules we measure a spectrum that shows the classical Gaussian distribution.

Two molecular ions 
Fragmentation→ cleavage of the chemical groups. Then the molecular weight of the cleaved group can be subtracted. Then the signals correspond to each molecule minus the groups that have been removed during fragmentation.

The fragmentation provides us with the original informaition.
-> slide ANALYTE IDENTIFICATION

Each molecule undergoes a specific fragmentation in the process which makes it possible ot identify it.

The three main components:
Ion source 
Analyzer
Detecter

A and D must be at 10^-6 millibar (vacuum)

MALDI
Matrix assisted laser assisted ion 
Sample - is SOLID cocrystallized in an aromatic acid to protect it from the ???
High energy. The aromatic groups can absorb the lasers energy.
Double role: protection and assisting the proces.
Matrix is added in excess.
Chromophoric acid that absorbes the lasers energy

TYPES OF ACIDS ARE NOT RELEVANT FOR THE EXAM

Orbitrap
Frequency dependent on m/z ratio.

ESI
Electron spray
at atmospheric pressure.
Dropplets become smaller 
One of the most sensitive tequnique - down to the atomolar level. 
BUT it requires a “sample cleanup” - no lipids, no salts!!!
Hyphenation - coupling


TOF
One of the best - sling shot
Same acceleration potential 
m/z=2Vt^2/L^2
Normal and Reflectron analyzer: slide.

MS Detectors
Follow the principle of diodes  - but instead of photons we have ions.

During ionization process -we can just ionize or both ionize and fragment the sample.

TANDEM MASS SPECTROMETY
Combines 2 or more mass analyzers or the smae or different types
The first one Analyzes the parent ion
Then it is fragmented
The second one obtains the mass spectrum of the fragments (daughter ion spectrum)



In the classical bottoma up approch
We can either opt for a soft ionization. Analyzer such as a TOV. Then we detect and analyze the peptides - 

Soft ionization in the first stage and selection of an ion. No fragmentation in the first step and thats why we introduce a collision cell between two analyzers

Ion source - MALDI
Fragmentation and then 

Q-TOF
TOF-TOF easiest to apply
Triple quadrople

Tandem MS is used to 
For complicated molecules such as proteins we have to first select the ions. 


Instead of heaving a second quadruple we have a TOF analyzer. This is one of the most used instruments for proteomics. It can be easily connected to HPLC.

Little digression Data bases

Web of science

Scopus

Espacenet

Experimental and insilico data need to be matched

For new stuff- no priro knowledge → de novo sequencing is necessary (Edman was gold standard but now it is Tandem mass spectrometry). Then you may also obtain information about the folding.

Bottom up approach

- peptide mass finger printing: we obtain almost a single protein level. (Single spot is taken from gel, purified with zip tip 
- shot gun approach: we are dealing with a more complex sample: multidimensional chromoatography - is a powerful sepparation tequnique (that replaces 2D gels).

We can identify up to 1000 proteins. 



Trypsin review:
- cheap
Wide temp and pH range
terminal???



What can we derive from the spectrum?

Experimental spectrum must be compared with the theoretical ones (proteins that are digested in silico). Resticting the search in the database.

2D electrophoresis → gives us the info of Ip and MW. This can help us to narrow down the search.



The theoretical ones will never match the experimental ones.
 
The missed cleavge site - depends on the efficiency of the enzyme

Positive and negative modality:
Phosphorylated proteins require negative modality????????????

2D Electrophoresis:
11.01 If we have alkylated cystein residues….??????????????? 

Threasholds are typical for the method???

Summary: all softwares have a colourcoding.

SLIDES: PMF basics

Loss of target molecules occur. For example by cleanup with zip tibs C_18 (and C_3?)
Lack of resolution also may be a problem. 

What are missed cleavages?
Trypsin will cut most of the time, but sometimes it will fail. So there is a list of tryptic cleavage sites where the missed sites are considered in the software.

Relative mass 
Monoisotopic mas is the mass of the most abundant isotopes.

Keep in mind that the mass of the residue is different from the aa.



The data base stores the info that each peptide be


The idea is to find a match - The query mass is defined by threasholds and so on.


The method has to be established and validated that takes weeks.

But MALDI may be used “by anybody” → so it is faster.

SLIDES:
PEPTIDE DE NOVO SEQUENCING
Is the current approach for obtaining aa from tandem ms without any previous knowledge.

The fragments are measured to produce the mass mass spectrum. MS/MS refers to the data being from a tandem type approach.

Some ions retain the charge on the N terminal while others do on the C terminal. This helps us to identify different types. AB - charge on the N terminal and XYZ have it on the C terminal.

B and Y are most common


The main idea of de novosequencing is to use the mass difference between two fragment ions to calculate the mass of an amino acid residue on the peptide backbone. The mass can usually uniquely determine the residue. For example, the mass difference between the y7 and y6 ions is equal to 129, which is the mass of residue E. Similarly, the next adjacent residue between y6 and y5 can be determined as L by the mass difference. 

In reality we have many complications - such as post translational modifications. 

The software assignes a confidence value.

As we have several uncontrollable variable. B and y peaks… ect.

What is a volcano plot???
Learn the types of representations: Venn, heatmap… → the peak software provides it.

PTM - post translational modificaitons may be added to the analysis of the program. That can be natural OR artificial: alkylation of the cystein. 
