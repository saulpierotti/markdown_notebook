% Laboratory of Bioinformatics 2
% Saul Pierotti
% \today

# Part 1 - Prof. Casadio

## Introduction
* When doing data analysis, check first the quality of your data and ask yourself if it is worth it analysing them
* In the real world you will mostly be alone, so learn to be independent
* You should be able to create your own tools when pre-made tools are not available
* Computational results need to be analysed in terms of their exportability ot the wet lab for validation
* Information increases by going from sequences to structures
* The CAF (critical assessment of functional annotation) is an important contest for functional annotation

## Secondary Structure
* In order to determine the secondary structure of a protein is important to have good resolution structures
	* From a good structure I can understand torsion angles
* jCE is not available anymore at the PDB, you can only do sequence alignments and not structural alignments
* For structural alignments we can use TopMatch (for pairwise) or Mustang (multiple)
* If I have a CryoEM structure the secondary structure is not easy to determin (depends on resolution)
* First problem: I have a crystal structure and I want to determine the secondary structure of a protein
* A 3d structure is a reduce representation of the electron density that collapses all the fuzzy electron density of a molecule to discrete atomic coordinates!
* It is easier to descibe secondary structure in terms of H bonds, not in terms of torsion angles
* First I need to locate the hydrogens, that are usually not seen at normal resolutions
	* H is transparent to X-rays
	* There are several algortihms for H embedding
		* A famous one was developped by Janet Thornton (EBI director)
		* Some algorithms are MolProbity and WHATIF
		* WHATIF was developped by a professor that now lives in the Filippines
	* Also molecular visualization software need to fill-in hydrogens to determine which secondary structure to show!
	* In general I can embed hydrogens by following simple chemical rules
* Once I have the hydrogen positions I can determine the secondary structure from the backbone H-bonding pattern among neighboring residues
* I can understand if there is an H bond between 2 C atoms by inspecting their distance (after placing the H)
* We will use the dssp algorithm for secondary structure assignment from 3d structure
* Torsion angles are not so easy to extract from 3d structures, so they are not the preferred way for secondary structure determination
* An H bond is present when the distance among the atoms involved is under 2 $\AA$ and the atoms are co-planar
	* H bonds can be formed in proteins mainly by O and N
* H bonding happens both in solvent accessible and inaccessible areas
* Side chains do not really determine secondary structure, so predicting secondary structures from sequence can be misleading
	* Propensities are only average properties
* Prediction of secondary structure is important since by assigning a good secondary structure to a sequence I can identify remote homologs
	* In superfamilies structure is conserved but not sequence
	* If structure is conserved and I can determine the secondary structure of a sequence, I can align secondary structure elements in order to identify remot homologs
* From this, I can maybe get a structural model for proteins lackingg obvious homolog structures in the PDB
	* I can obtain the secondary structure of all the PDB structures using dssp or similar algorithms
	* I can predict the secondary structure of my sequence
	* I can try to find a structural template for my protein by  aligning secondary structure elements and finding a protein with similar topology (irrespective of sequence)
* The topology of a protein is the order succession of secondary structurer elements
* Predicting secondary structure means mapping a 20-charachtr alphabet to a 3-charachter alphabet (H, E, C)
* Also here, after I am able to assign a structure to my protein I can trasfer annotation from the template: I can do functional annotation
* To date SS predictors are all top-scoring, so there is not much to improve
	* Accuracy is currently $0.8$ to $0.9$
	* Burckhard Rost suggested in a paper that we are at an hard limit of accuracy since we are limited by uncertainty in the original structural data

## Helices
* Alpha helices are self-organizing local structures
	* They are local in the sense that they do not involve long-range interactions
* In alpha helices the H-bonding happens among residues in position $i$ and $i+4$
* The minimum lenght for an helix is thus 4 residues
* There is no real maximum lenght, there are fibers that are even 500 residues long
* Alpha-helices are dextrose
* A summary of helices dimensions

|                  | $\alpha$ helix | $3_{10}$ helix | $\pi$ helix |
|------------------|---------------:|---------------:|------------:|
|Residues per turn | 3.6    aa      | 1.0    aa      | 4.4    aa    |
|Step per residue  | 1.5 $\AA$      | 2.0 $\AA$      | 1.1 $\AA$   |
|Radius            | 2.3 $\AA$      | 1.9 $\AA$      | 2.8 $\AA$   |
|Pitch             | 5.4 $\AA$      | 6.0 $\AA$      | 4.8 $\AA$   |

## Strands
* Beta sheets are not local since they require the interaction of beta strands that can also be far in the sequence
* The minimun length for a strend is 2 residues (Prof. Casadio did the statistics on the PDB)
* Knowing the minimum length is important in order to assess the reliability of predictions and implement filters

## $\Delta\Delta G$
* A major source of stability for a protein is its $\Delta G$ of folding
* The $\Delta G$ of folding can be measured in vitro
* The difference in $\Delta G$ of folding among 2 variants of the same protein is called $\Delta \Delta G$ of folding of that variation
* A variant shares most of the prilmary sequence with the original protein, and it can change at most in a couple of positions or present indels
* Note that $\Delta G$ is an experimentally measured quantity with a SD of around $\pm 1 kcal/mol$ with current experimental technique
	* When calculating a $\Delta \Delta G$ aware of this!
	* The $\Delta G$ of folding can range from $0$ to $-50 kcal/mol$
	* A $\Delta G$ of $0 kcal/mol$ does not mean much when it is affected by an error of $\pm 1 kcal/mol$!
* If $\Delta \Delta G > 1 kcal/mol$ I have an increase in protein stability for the variant with respect to the original protein
* If $-1 < \Delta \Delta G < 1 kcal/mol$ the variant does not affect protein stability
* If $\Delta \Delta G < -1 kcal/mol$ I have a decrease in protein stability for the variant with respect to the original protein

## UniProt Biocuration
* UniProt/TrEMBL is annotated manually contributing to SwissProt
	* Protein/Genes in UniProt are first screened to remove redundancies
	* A sequence analysis step is performed using predictors and expert systems (Pfam, InterPro, ...)
		* I am here predicting sequence features
	* Literature is mined to establish links between assertions and experimental evidence
		* This is a combination of text mining and actual people reading the papers
	* Curation based on protein families (annotation transfer)
	* Evidence attribution for individal claims
	* Quality assurance before integration into SwissProt
		* Here the annotation score is assigned
	* The PDB structure is included (if it exists)
* SwissProt is used then for the automatic annotation of UniProt
	* Templates are identified by sequence alignment
	* Build rules that define conditions to be respected for the transfer of annotation
		* SAAS (Statistical Automatic Annotation System) is used for the automatic generation of annotation rules 
			* It is a decision tree
		* UniRule is a set of manually created rules (If...Else statements)
	* The new rules are checked against SwissProt for validation before being applied
	* The rules are used for the automatic annotation of UniProt
* TrEMBL is obtained by automatic translation of EMBL
	* Finding CDSs on genomic data is not trivial
* Only 5% of the UniProt entries are obtained directly from the sequencing of proteins
* Particularly in TrEMBL, annotation can change drammatically among DB version
	* This is due to the update of UniRule and SAAS
* Since release 2020_04 SAAS has been replaced with ARBA (Annotation-Rule Based Annotator)
	* It is a multiclass learning system trained on SwissProt etries
	* It uses rule-mining techniques to generate human-readable annotation rules
	* It maintains a set of exclusion rules for properties that cannot be efficiently automatically annotated
* Each annotation in UniProt reports an evidence tag that assert how that annotation was obtained (experimental evidence or prediction)
	* This tag system is called ECO, and it is similar ot GO terms (it is an acyclic graph of descriptors)


## Short Range Interactions
* H bonds are long around $2 \AA$ and have an energy of $10 kcal/mol$
	* The bond energy is roughly proportional to the squared distance of the atoms
* Van der Waals interactions (London dispersion energy) are among induced dipoles
	* They are heavily depend on distance $r^{-6}$
* Salt bridges are charged-charged particle interactions
	* Their strenght depends on the environment (at the core or in the solvent)
	* They depend on $r$
* Rotating dipole interactions are temperature dependent

## InterPro
* InterPro is a consortium of many different predictors that converge in the annotation of proteins and families
* It is now at version 82, it is frequently updated!
* Pfam is included in InterPro, and kind of performs the same function

## DSSP (Define Secondary Structure of Proteins)
* DSSP (Kabasch and Sanders) is used for the definitiion of secondary structure in many molecular visualization software

---

# Part 2 - Prof. Savojardo

## Introduction to the Project
* Here we will extend our practice in functional annotation with a project
* We will compare the GOR method and SVM for the prediction of secondary structure form sequence
* We will be provided with data (fasta sequences and dssp assignments) and CV splits
* We will need to generate a testing set from the PDB database
* We will prepare our data and implement the GOR and SVM predictors
* We will discuss critically the results and write a manuscript
* The manuscript should be compliant with the OUP Bioinformatics journal guidelines

## Vritual Machine Configuration
* All the computationally-intensive tasks will be done in a VM that they will provide
	* The VM has 2 cores, 8 Gb of RAM, 50 Gb of HDD
	* All the software needed will be available in a conda environment
* The VMs will be accessed through a VPN and SSH
* When you close a terminal, you also close all of its child processes
* In order to let computationally-intensive tasks run while disconnected from the VM we will use screen
	* It is possible also to use nohup or at
* Screen is a terminal  multiplexer: you can start a screen session and then into it start as many virtual terminals as you want
* Screen sessions are persistent when the terminal that originated them is closed
* A new screen session is created with the command `screen`, which also creates a window inside the session and starts a shell into it
* To detach from the current session I press `Ctrl+a d`
* I can list detached sessions with `screen -ls`
* I can reattach a detached session with `screen -r`
* I can create a new window in the same session with `Ctrl+a c`
* I can list all the windows in the current session with `Ctrl+a "`
* I can show an help with `Ctrl+a ?`






---

* 



















# Secondary Structure
* Secondary structures are local motives of order
* JCE has been removed from the PDB website
* I can use TopMatch for pairwise structural alignment, and Mustang for multiple structural alignment
* H is usually not visible in 3D structures, since it needs a resolution better than 1 $\AA$
* Molecular visualization softwares in order to show secondary structure use algorithms that compute the position of hydrogens
	* Jahnet Tornhton developped one of the most used algorithms
* A protein is a stable entity when there is the right combination of residues that allow the backbone to fold in the solvent space
* An hydrogen bond is on average $2 \AA$ long
* The atoms involved in the H bonding should be strongly electronegative
	* The H is in a frustrated, unstable position
* In an alpha-helix H bonds occur with the 4th following residue
* H-bonding happens both in solvent-accessible and solvent-unaccessible regions
* Protein with the same secondary structure topology are probably similar also in tertiary structure
	* This is in spite of primary structure
* HMMs can be used to model domains, not entire proteins
* Comparing protein topology allows to predict the structure of entire proteins
* If you are lost for a protein, predict its secondary structure and allign it against the PDB filtered so to apper as a set of secondary structures
* The accuracy of secondary structure predictors is around 80-90%
	* According to Rost this accuracy is an upper limit, given the resolution of the atomic coordinates of proteins
* An helix is at least 4 residues long, while a strand is at least 2 residues long
* There is no upper limit, but there are helices in fibers which are several hundred residues long
* The topology is the organization in space of all the secondary structure motives of a protein
	* For our purpose it is all the different patterns of secondary structure from the N to C terminus
* When using a sliding window, the central residue of the window is assigned the average value of the entire window
	* This causes a smoothing of the values across a sequence
* Local features are better grapsed by sliding windows
* HMMs are not suitable for modelling local features like secondary structures
* Chamelion segments are combinations of residues that can be found in different secondary structures

## Protein Stability
* A genetic variant of a protein (an allele with a single aminoacid difference) can have a different stability than the original protein allele
* A variation in $\Delta G$ among 2 proteins due to a genetic variant, called $\Delta \Delta G$ can increase or decrease protein stability
$$ \Delta \Delta G = \Delta G_{mut}-\Delta G_{nat}$$
	* If $\Delta \Delta G > 1.0$ the variation increases protein stability
	* If $\Delta \Delta G < -1.0$ the variation decreases protein stability
	* If $\Delta \Delta G < -1.0$ the variation decreases protein stability
	* If $1.0 < \Delta \Delta G < 1.0$ the variation has little effect on protien stability

## Hydrogens in Macromolecular Models
* See `https://proteopedia.org/wiki/index.php/Hydrogen_in_macromolecular_models`
* Approximately 50% or protein atoms and 35% of nucleic acids atoms are hydrogens
* Most crystals do not have sufficient resolution (1.0 Ångstroms or better is needed) to determine the positions of hydrogen atoms directly
* It is easy to add hydrogens to macromolecular models, but the results are only as good as the molecular models themselves
* High resolution protein crystallography (1.2 Ångstroms or better) can assign some hydrogen positions empirically from the electron density map, and very high resolution crystals (1.0 Ångstroms or better) can assign the positions of most hydrogens
* It is easy to add hydrogens to macromolecular models (PDB files) using the highly-reliable free servers MolProbity and WHATIF

## Uniprot
* Annotation in UniProt is manual and automatic
* SwissPort includes only manually reviewed proteis, despite their annotation quality
* Automatic annotation is based on UniRule and SAAS
* UniRule rules are made by expert curators, while SAAS rules are automatically generated
* SAAS uses machine learning to create rules from analysing manually and UniRule annotated entries

## DSSP
* DSSP is an algorithm developped by Sander and Kabasch in 1983 for the assignment of secondary structure to 3D structures
	* First hydrogens are added according to the chemical properties of elements
	* Then DSSP uses a purely electrostatic definition to assign hydrogen bonding patterns and, from this, secondary structure
* The DSS algorithm is embedded in many visualization softwares
* The goal of DSSP is to approximate the intuitive concept of secondary structure with an objective algorithm
* Extracting structural features from a set of coordinates is a pattern recognition process
* Using torsion angles for assessing secondary structure requires many parameters, while using the presence of hydrogen bonds requires a single parameter: bond lenght
	* Torsion angles are defined using the position of 4 atoms each
* n-turns are defined by the presence of an H-bind between the CO of residue $i$ and the NH of residue $i+n$, with $n=3,4,5$
* Bridges are defined similarly to turns, but for $n>5$
* Bridges are also required to be at least 3 residues long
* Alpha helices are described by repeating 4-turns, while beta structures are defined by repeating bridges
* A series of 3-turns describes a 3:10 helix, while a series of 5-turns describes a $\pi$ helix
* Other structures such as 3-10 helices, $\pi$ helices, single turns, and single beta bridges are derived from combinations of these fundamental elements
* Bends, chirality, and solvent exposure are defined geometrically
* Each feature is assigned independently and structural overlaps are resolved by defining a summary that assigns a single state to each residue
* H bonds in proteins have little wave-function overlap and can be descrobed with purely electrostatic terms
* Partial charges are placed in the H bonding groups
	* C is assigned +0.42 eV, O -0.42 eV
	* N is assigned -0.20 eV, H +0.20 eV
* The electrostatic interaction is then calculated as
$$E = q_1q_2(\frac{1}{r_{ON}}+\frac{1}{r_{CH}}-\frac{1}{r_{OH}}-\frac{1}{r_{CN}})*f$$
* A good H bond as an energy of -3 kcal/mol, but the cutoff used is -0.5 kcal/mol to account for errors in coordinates and bifurcated bonds
* There is no universally accepted H bond definition, so a description is necessarily tailored to a purpose
	* Their definition demonstrated to be adequate for the purpose
* Imperfections in helices are allowed in order to account for kinks
* Bends are assigned to regions with a curvature of more than 70° along 5 consecutive residues
	* The bend is assigned to the central of 5 residues
* Chirality is defined at each residue (except chain ends) as the sign of the dihedral angle among 4 consecutive Ca
* SS bonds are taken directly from the PDB record, since they can be considered part of the primary structure
* Chain breaks are assumed for peptide bonds longer than 2.5 $\AA$
* Structural overlaps are resolved with a priority rule
* Each secondary structure is assigned a code, that is also used in many applications outside of DSSP
	* G is a 3:10 helix of at least 3 residues
	* H is an alpha helix of at least 4 residues
	* I is an $\pi$ helix of at least 5 residues
	* T is a turn (3,4, or 5 turn)
	* E is an extended strand (parallel or antiparallel) in beta conformation, at least 2 residues long
	* B is an isolated bridge of 1 residue
	* S is a bend, assigned not according to H bonds but to geometry
	* C is a coil, a residue in none of the above conformations
	* Other categories exist, but are rarely used
* DSSP is generally accepted as a tool for assigning secondary structure
* I can get solvent exposure values that are higher than expected when heteroatoms are present, since they are ignored
* I can get solvent exposure values that are lower than expected when oligomers are present, since the exposure is calculated for the oligomer and not for the monomer
# LB2 Project
* We will compare 2 different approaches for predicting protein secondary structure
	* The GOR method, based on statistical analysis
	* Using SVM (background from Martelli)
* We will be given the training data and the cross-validation splits
* Training data are FASTA files and DSSP secondary structures
* We will implement everything in python
* They will provide us a virtual machine with linux with 8 Gb RAM and 50 Gb HDD, with all the necessary software installed in conda

# Neural Networks
* McCulloch e Pitts (1943) modeled a neuron as an object receiving an input vector and producing a scalar output via linar combination of the inputs (with weights), transformed by a transfer function
* A simple perceptron has just an input layer and an output layer, and operates only in a feed-forward manner
* A multi-layer perceptron contain hidden layers of neurons
* A NN is an alternative computational paradigm in which the solution to a problem is automatically learned from a set of examples
* A NN performs general non-linear mapping
* A single-layer perceptron performs a total summation of the inputs $x_i$, each associated with a weight $w_i$, in order to determine the activation $a$, and the output $z$ after applying the transfer function $g(a)$
$$a=\sum_i w_i x_i$$
$$z = g(a)$$
	* The bias of the neuron is usually represented as an additional input $x_0$
* The error function of the perceptron is proportional to the sum of squared differences between predicted and real values, over all the training examples and over all the output neurons
* For the single training point $X^q$, if $D_i^q$ is the real desired value of example $q$ for output neuron $i$
$$ E^q = \frac{1}{2} \sum_i (Y_i(X^q)-D_i^q)^2$$
* The NN reaches an optimal configuration when its error function is minimal

# Protein Phase Separation

