% Laboratory of Bioinformatics 2
% Saul Pierotti
% \today

# Part 1 - Prof. Casadio

## Introduction

- When doing data analysis, check first the quality of your data and ask yourself if it is worth it analysing them
- In the real world you will mostly be alone, so learn to be independent
- You should be able to create your own tools when pre-made tools are not available
- Computational results need to be analysed in terms of their exportability ot the wet lab for validation
- Information increases by going from sequences to structures
- The CAF (critical assessment of functional annotation) is an important contest for functional annotation
- Levitt was a pioneer in molecular dynamics and won a Nobel prize in 2013
- Homogeneity of the data is a prerequisite if you want to compare your resoults with other people
  - If I want to predict secondary structure, it is important that we all use the same kind of assignments as labels (dssp)
- A PDB structure is a reduced representation of a protein
- In order to calculate the contact surfa among 2 proteins I can just evaluate the difference in solvent accessible area upon binding
- A new protein family can be defined when a structure with a totally new fold is discovered
  - This is really rare but possible
- If you want to find a job look at databases, if you are good enough swtich to computational biology and develop algorithms
- Database numbers (24/11/2020)

|           |             |            |
| --------- | ----------: | ---------- |
| UniProt   | 195 104 019 | proteins   |
| SwissProt |     563 552 | proteins   |
| PDB       |     171 313 | structures |
| Pfam      |      18 259 | families   |

## Secondary Structure

- In order to determine the secondary structure of a protein is important to have good resolution structures
  - From a good structure I can understand torsion angles
- jCE is not available anymore at the PDB, you can only do sequence alignments and not structural alignments
- For structural alignments we can use TopMatch (for pairwise) or Mustang (multiple)
- If I have a CryoEM structure the secondary structure is not easy to determin (depends on resolution)
- First problem: I have a crystal structure and I want to determine the secondary structure of a protein
- A 3d structure is a reduce representation of the electron density that collapses all the fuzzy electron density of a molecule to discrete atomic coordinates!
- It is easier to descibe secondary structure in terms of H bonds, not in terms of torsion angles
- First I need to locate the hydrogens, that are usually not seen at normal resolutions
  - H is transparent to X-rays
  - There are several algortihms for H embedding
    - A famous one was developped by Janet Thornton (EBI director)
    - Some algorithms are MolProbity and WHATIF
    - WHATIF was developped by a professor that now lives in the Filippines
  - Also molecular visualization software need to fill-in hydrogens to determine which secondary structure to show!
  - In general I can embed hydrogens by following simple chemical rules
- Once I have the hydrogen positions I can determine the secondary structure from the backbone H-bonding pattern among neighboring residues
- I can understand if there is an H bond between 2 C atoms by inspecting their distance (after placing the H)
- We will use the dssp algorithm for secondary structure assignment from 3d structure
- Torsion angles are not so easy to extract from 3d structures, so they are not the preferred way for secondary structure determination
- An H bond is present when the distance among the atoms involved is under 2 $\AA$ and the atoms are co-planar
  - H bonds can be formed in proteins mainly by O and N
- H bonding happens both in solvent accessible and inaccessible areas
- Side chains do not really determine secondary structure, so predicting secondary structures from sequence can be misleading
  - Propensities are only average properties
- Prediction of secondary structure is important since by assigning a good secondary structure to a sequence I can identify remote homologs
  - In superfamilies structure is conserved but not sequence
  - If structure is conserved and I can determine the secondary structure of a sequence, I can align secondary structure elements in order to identify remot homologs
- From this, I can maybe get a structural model for proteins lackingg obvious homolog structures in the PDB
  - I can obtain the secondary structure of all the PDB structures using dssp or similar algorithms
  - I can predict the secondary structure of my sequence
  - I can try to find a structural template for my protein by aligning secondary structure elements and finding a protein with similar topology (irrespective of sequence)
- The topology of a protein is the order succession of secondary structurer elements
- Predicting secondary structure means mapping a 20-charachtr alphabet to a 3-charachter alphabet (H, E, C)
- Also here, after I am able to assign a structure to my protein I can trasfer annotation from the template: I can do functional annotation
- To date SS predictors are all top-scoring, so there is not much to improve
  - Accuracy is currently $0.8$ to $0.9$
  - Burckhard Rost suggested in a paper that we are at an hard limit of accuracy since we are limited by uncertainty in the original structural data
- Secondary structures are cooperative
- A secondaary structure is a local motive of order
- There are at least 8 types of secondary structures
- Helices tend to be easier to predict than strands and coils
  - Sliding windows are grasping the context surrounding the predicted conformation
  - Since helices are local structures (as compared to strands), they can be better predicted by a sliding window system
- A chamelion segment is a sliding window configuration that can be found in different configurations
- A sliding window-based approach can discriminate chamelion segments only if they are shorter of sliding window!
- Today, if you need a secondary structure use Jpred (it gives quality scores) or PsiPred (it does not)

## Helices

- Alpha helices are self-organizing local structures
  - They are local in the sense that they do not involve long-range interactions
- In alpha helices the H-bonding happens among residues in position $i$ and $i+4$
- The minimum lenght for an helix is thus 4 residues
- There is no real maximum lenght, there are fibers that are even 500 residues long
- Alpha-helices are dextrose
- A summary of helices dimensions

|                   | $\alpha$ helix | $3_{10}$ helix | $\pi$ helix |
| ----------------- | -------------: | -------------: | ----------: |
| Residues per turn |         3.6 aa |         1.0 aa |      4.4 aa |
| Step per residue  |      1.5 $\AA$ |      2.0 $\AA$ |   1.1 $\AA$ |
| Radius            |      2.3 $\AA$ |      1.9 $\AA$ |   2.8 $\AA$ |
| Pitch             |      5.4 $\AA$ |      6.0 $\AA$ |   4.8 $\AA$ |

## Strands

- Beta sheets are not local since they require the interaction of beta strands that can also be far in the sequence
- The minimun length for a strend is 2 residues (Prof. Casadio did the statistics on the PDB)
- Knowing the minimum length is important in order to assess the reliability of predictions and implement filters

## $\Delta\Delta G$

- A major source of stability for a protein is its $\Delta G$ of folding
- The $\Delta G$ of folding can be measured in vitro
- The difference in $\Delta G$ of folding among 2 variants of the same protein is called $\Delta \Delta G$ of folding of that variation
- A variant shares most of the prilmary sequence with the original protein, and it can change at most in a couple of positions or present indels
- Note that $\Delta G$ is an experimentally measured quantity with a SD of around $\pm 1 kcal/mol$ with current experimental technique
  - When calculating a $\Delta \Delta G$ aware of this!
  - The $\Delta G$ of folding can range from $0$ to $-50 kcal/mol$
  - A $\Delta G$ of $0 kcal/mol$ does not mean much when it is affected by an error of $\pm 1 kcal/mol$!
- If $\Delta \Delta G > 1 kcal/mol$ I have an increase in protein stability for the variant with respect to the original protein
- If $-1 < \Delta \Delta G < 1 kcal/mol$ the variant does not affect protein stability
- If $\Delta \Delta G < -1 kcal/mol$ I have a decrease in protein stability for the variant with respect to the original protein

## UniProt Biocuration

- UniProt/TrEMBL is annotated manually contributing to SwissProt
  - Protein/Genes in UniProt are first screened to remove redundancies
  - A sequence analysis step is performed using predictors and expert systems (Pfam, InterPro, ...)
    - I am here predicting sequence features
  - Literature is mined to establish links between assertions and experimental evidence
    - This is a combination of text mining and actual people reading the papers
  - Curation based on protein families (annotation transfer)
  - Evidence attribution for individal claims
  - Quality assurance before integration into SwissProt
    - Here the annotation score is assigned
  - The PDB structure is included (if it exists)
- SwissProt is used then for the automatic annotation of UniProt
  - Templates are identified by sequence alignment
  - Build rules that define conditions to be respected for the transfer of annotation
    - SAAS (Statistical Automatic Annotation System) is used for the automatic generation of annotation rules
      - It is a decision tree
    - UniRule is a set of manually created rules (If...Else statements)
  - The new rules are checked against SwissProt for validation before being applied
  - The rules are used for the automatic annotation of UniProt
- TrEMBL is obtained by automatic translation of EMBL
  - Finding CDSs on genomic data is not trivial
- Only 5% of the UniProt entries are obtained directly from the sequencing of proteins
- Particularly in TrEMBL, annotation can change drammatically among DB version
  - This is due to the update of UniRule and SAAS
- Since release 2020_04 SAAS has been replaced with ARBA (Annotation-Rule Based Annotator)
  - It is a multiclass learning system trained on SwissProt etries
  - It uses rule-mining techniques to generate human-readable annotation rules
  - It maintains a set of exclusion rules for properties that cannot be efficiently automatically annotated
- Each annotation in UniProt reports an evidence tag that assert how that annotation was obtained (experimental evidence or prediction)
  - This tag system is called ECO, and it is similar ot GO terms (it is an acyclic graph of descriptors)

## Short Range Interactions

- H bonds are long around $2 \AA$ and have an energy of $10 kcal/mol$
  - The bond energy is roughly proportional to the squared distance of the atoms
- Van der Waals interactions (London dispersion energy) are among induced dipoles
  - They are heavily depend on distance $r^{-6}$
- Salt bridges are charged-charged particle interactions
  - Their strenght depends on the environment (at the core or in the solvent)
  - They depend on $r$
- Rotating dipole interactions are temperature dependent

## InterPro

- InterPro is a consortium of many different predictors that converge in the annotation of proteins and families
- It is now at version 82, it is frequently updated!
- Pfam is included in InterPro, and kind of performs the same function

## DSSP (Define Secondary Structure of Proteins)

- DSSP (Kabasch and Sanders, Heidelberg) is used for the definitiion of secondary structure in many molecular visualization software
- The recognition of secondary structure is based on a set of criteria, not laws
- Recognizing secondary structure is a pattern recognition process on H bonds
- DSSP is not the only SS predictor from structure, but it is very simple and one of the most used
  - It inspired another predictor, Stride
  - It is used by basically all the molecular visualization softwares
- The DSSP paper is from 1983, and the first PDB deposition was done in the 70's
- DSSP approximates secondary structures with an objective function
- DSSP uses H bonds as a defining feature and not torsion angles or atomic coordinates, since these can be defined by a single parameters (bond energy cutoff)
- An $n$-turn is defined as an H bond between the CO of residue $i$ and the NH of residue $i+n$, with $n \in \{3,4,5\}$
- An H bond between residues not near to each other in the sequence defines a bridge
- Turns and bridges essentially exhaust all the possible interactions among backbone atoms
- DSSP was originally written in Pascal
- The current version was written by the authors of WHATIF (Maarten Hekkelman) and it is in C++
- The definition of secondary structure is hierarchical: H bonds define turns and bridges, and they define helices and ladders
- DSSP assigns a secondary structure to each residue
- H bonds are assumed to be present if they have an energy lower than $-0.5 kcal/mol$
  - A good H bond is said in the paper to be of about $-3 kcal/mol$
- The energy of H bonds is represented with a heuristic equation (electrostatic model, not quantistic)
- The cutoff chosen is permissive to allow for bifurcated H bonds and errors in the coordinates
- There is no generally correct H bond definition since there is not sharp transition from the quantistic definition (that dominates at short distances) and the electrostatic definition (that dominates at larger distances)
- The angular flexibility was limited to 60°
- Helices are represented with H in the output of DSSP, ladders with E (extended)
- A series of turns is an helix, a series of bridges is a ladder
- A bend is an angle in which the $C_\alpha$ in position $i$ and $i+2$ form an angle higher than $70°$
- In practice, everithing that is not an helix or a strand will be considered and represented as a coil (C, or -)
  - This includes bends!
- Most helices have positive chirality (right-handedness) while strands have negative chirality
- As an addendum, DSSP can determine the solvent accessible area of a protein
  - The solvent exposure calculated is static since it does not include the movent of the protein
  - The dynamic movent of the protein can alter which portions are accessible!
  - Physically, we are interested in the number of water molecules in direct contact with the protein
  - Geometrically, I can roll a sphere representing a water molecule on the surface of the protein and record the positions touched
    - The surface is proportional to the number of water molecules in the first hydratation shell

## Neural Networks

- Neural networks are inspired by biological neurons
- McCulloch e Pitts (1943) modeled a neuron as an object receiving an input vector and producing a scalar output via linear combination of the inputs (with weights neign the linear coefficients), transformed by a transfer function
- A treshold can be considered as just an additional neuron
- A simple perceptron has just an input layer and an output layer, and operates only in a feed-forward manner
- A multi-layer perceptron contain hidden layers of neurons with only feed-forward connections
- A NN is an alternative computational paradigm in which the solution to a problem is automatically learned from a set of examples
- A NN performs general non-linear functional mapping (from an input to an output space)
- Any model relates variables by the means of parameters
- A single-layer perceptron performs a total summation of the inputs $x_i$, each associated with a weight $w_i$, in order to determine the activation $a$, and the output $z$ after applying the transfer function $g(a)$
  $$a=\sum_i w_i x_i$$
  $$z = g(a)$$
  - The bias of the neuron is usually represented as an additional input $x_0$
- The error function of the perceptron is proportional to the sum of squared differences between predicted and real values, over all the training examples and over all the output neurons
- For the single training point $X^q$, if $D_i^q$ is the real desired value of example $q$ for output neuron $i$
  $$ E^q = \frac{1}{2} \sum_i (Y_i(X^q)-D_i^q)^2$$
- The NN reaches an optimal configuration when its error function is minimal
- The backpropagation algorithm was invented by Rumelhart when he was a PhD student in 1986
  - It is a gradient descent algorithm
  - It updates the weight by subtracting to the previous weigths the derivative of the error function with respect to the weight (times the learning rate $\eta$) and adding a momentum term
  - The momentum term is the previous update to the weights times the hypeerparameter $\mu$
- The input size of the network is in general, for sequences, the size of the sliding window applied
- Neural Networks are convenient when an analitical solution for my problem is not available
- I need a lot of data, and data of a very good quality
  - Before starting any machine learning approach, check data quality
- Many journals require specific cross-validation procedures for ML papers
- As for ML approaches input is it better to use profiles instead of sequences
- Transfer functions can be linear, stepwise, sigmoid
- Neural Networks can perform a non linear functional mapping thanks to their nonlinear tranfer function
- In order to update the weights in the backpropagation algorithm I use the derivative of the error function with respect to the weights
- It is important for tranfer functions to be continuous in order to make the error function derivable
- The derivative of the sigmoid is the sigmoid itself, so it is really handy in computations for calculating higher derivatives
  - It is not like this, but so she thinks
  - It is $\sigma(x)(1-\sigma(x))$ where $\sigma(x)$ is the sigmoid itself
- Why SVM and NN for predicting protein secondary structure and not HMM?
  - HMMs are global models for sequences, and they are useful for predicting global properties like domains
  - ML approaches are local (use a sliding window) and so are better for predicting a local motive of order like secondary structures

## Score Indexes

- The scoring accuracy is the fraction of correct predictions
  $$Q_1 = \sum_i P_i/N$$
- The Matthews correlation coefficient is a correlation coefficient for the classes
  - It is not affected by class umbalance
- The segment overlap measure (SOV) is used for the prediction of sequences
  $$SOV = \sum_s \frac{S_1 \cap S_2}{S_1 \cup S_2} \frac{L_1}{N}$$
  _ It can be defined in at least 3 different ways
  _ She expect us to put it in the project
  _ It is a measure of the correct superimposition of characters
  _ It should be calculated for H, E, and C (the term s in the sum) and summed
- Many predictors return also a reliability index for each position in the sequence (in the range 0-9)
  - In NN I can just derive it from the activations of the output layer by subtracting the best output (the highest) to the second best
  - It is proven that in a NN the output of a network is the probability of a certain answer

## History of Secondary Structure Prediction

- Secondary structures were predicted by Linus Pauling and Robert Corey in 1951 on the basis of H bonding and cooperativity criteria, before the first crystal structure
  - Pauling got the Nobel prize in chemistry 1954 (for secondary structures!) and in 1962
- NN proved to be the best tool for predicting secondary structure
- The prediction of secondary structure is a bioinformatics success story
- The first attempt at SS prediction was in 1957
- Myoglobin was the first prtoein to be solved at atomic resolution in 1960
- The PDB was born in 1973 with 15 structures
- First generation SS prediction methods (1960-1970) were based on single residue propensities, often averaged over a sliding window
  - An example is the Chou-Fasman method
- Second generation methods (1970-1990) were based on joint probabilities, and so started to investigate the context in which residues were found
  - Here they started also to use NN
  - An example is the GOR method
  - Accuracy stalled at 60%
- Third generation methods (1990) integrate evolutionary information by using sequence profiles
  - They were the first to break 70% accuracy
  - Seminal Rost and Sanders 1994 paper
- These generations actually do not only apply to secondary structure prediction, but in general to many prediction methods of protein properties

### First Generation Methods

- They are based on the computation of the frequency of occurrence of a residue in relation to a given feature
- A sliding window is a way for searching for emerging properties in a context
  - I can associate a property to each sliding window, and I can consider it as an emerging property of the window
- ProtScale is a website at ExPasy where I can input a sequence (or an identifier) and I get a series of sequence properties
  - I can get molecular weight, different propensities, ...
  - I can get all the properties averaged over a sliding window (that I can choose)
  - I can also decide the summarization method over the sliding window
- The Kite-Doolittle scale is an average of several hydrophobicity scales (including a partition coefficient) and it is provided at ProtScale
- The Chou-Fasman scale is also in ProtScale
- For proteins sliding windows are usually between 3 and 24 residues long
  - A really long window loses in resolution
  - A small sliding window is too noisy
- Using sliding windows I can see the emergence of regions with certain properties
- Chou-Fasman uses an heuristic for resolving inconsistencies (regions with more than 1 propensity)

### Second Generation Methods

- Here wee take explicitly advantage of the context

### Third Generation Methods

- Here we integrate evolutionary information in the form of sequence profiles
- Neural networks learn the mapping from sequence to secondary structure
- I want to use NN when I am not able to provide a simple first principle or a model based solution
- A sliding window on a profile is a matrix, and it is used as input for ML approaches
- Each weight multiplies one vector of that matrix
- Suppose that a first NN gives me an answer with a single residue in H conformation
  - I could use its output as input for another network in order to filter out these spourios alignments
  - This is equivalent to adding layers to the network
- I can use a collection of NN that, for instance, work on different sliding window sizes (or only discriminate one conformation), and then use an ensemble method to get an answer
- The biocomp group created secpred in the past
- Psipred was created at UCL at can predict, among other things, SS
  - The original was a NN, then it switched to SVM and now maybe itwill switch to deep learning
  - When the sequence has a structure, they just give the dssp answer

## Bologna Annotation Resource (BAR)

- Data validation is essential in predictions
- Experiments to validate protein predictions are lengthy and costly
- It is possible that 80% of the entries in UniProt are crap
- Protein function can be described with GO terms (cellular component, biological process, molecular function), EC numbers
- Each GO term has a tag referring to the way it was annotated (prediction or experimental evidence)
  - When doing prediction train only with experimental data
  - If you train on noise you get noise squared
- If sequence identity with an annotated template is above 80%, I can most probably just transfer the annotation
  - For molecular function I can transfer quite easily
  - For cellular component check if the organisms are both eukariotes!
- For identity above 30% I can say that 2 proteins have a similar structure, but I cannot say much for the function
- Similarity searches can be done with BLAST, Psi-BLAST, or Pfam (with HMMs)
- Professor Casadio became famous since she was able to predict the structure of membrane proteins
- Once they published a prediction that, after the crystal was published, was shown to be wrong (1 helics more)
  - That protein belonged to a family without any structure
- Since then, she decided to be very conservative about predictions
- Her group was given money to use a GRID as large as Emilia Romagna
- They used 30 million sequence from UniProt
  - If you filter out fragments and duplicates UniProt becomes much smaller
- They alligned all those sequences pairwise to create a network of sequences that they called BAR+
- Today they repeated with more sequences and released BAR+
- For the alignment they used BLAST
  - Even if BLAST is a local alignment tool, they were able to use it by forcing a minimum alignment lenght
- They called this network the protein sequence universe
- Many proteins in UniProt have some kind of annotation (PDB, GO, Pfam annotation)
- On the other side, I have all the poorly annotated NCBI proteomes
- They creatad a sequence similarity network by linking all the sequences that, pairwise, have identity higher than 40% and minimum reciprocal coverage of 90%
- Each connected component of the network forms a cluster
- The statistically validated the annotation of each cluster and trasfered annotations to all the cluster members
- From each cluster I can get an HMM by alligning members of the cluster that have a structure and members directly connected to them
- Once I have the HMM I can use it to align sequences to it and use modeler to get a structural model
- Now they are trying to trasfer also EC numbers
- BAR contains millions of clusters!
- To statistically validatej each annotation they did bootstrapping and calculated a p-value, and corrected it with Bonferroni
- There are around 10k cluster HMMs in BAR
- 23% of the sequences are in cluster that have a PDB!
- By setting a p-value thershold of 0.01, they were able to increase the nnotation of TrEMBL by 54%!
- In very large cluster, you can use a community detection algorithm to identify sub-clusters
- For some enzymes, sub-clusters have different specificities!
- They took part at the CAFA challange on functional annotation with BAR
- BAR allows to find the protein types that are most common in different genomes and to do sequence annotation
- I can transfer annotation among sequences with low similarity thanks to the intermediate alignments in BAR
- Different BAR clusters can belong to the same family

## The Multi-Dimensional Problem of Protein-Protein Interactions

- Castrense devolepped the latest PPI predictiors
- It is possibles to annotate proteins by predicting their interacting partners
- PPI predictions are one of the main bioinformatics fields where ML is used
- Macromolecular crowding is underapprectiated
- Protein phase separation: at high enough concentration of proteins in solution in the cytoplasm, the protein phase can separate
  - We observe aggregates of proteins
  - This is a well known chemical phenomenon called liquid phase separation
- An important question is if liquid phase separation has a biological role (in favoring PPIs)
  - This is membrane-less compartimentalization
- Protein flexibility may allow proteins to aggregate with different partners
- An aggregate can be a single complex or a full metabolic pathway
- Single cell sequencing is the future since it does not average over a large number of cells
- Data quality is highly strategic, and there are companies specialised in measuring it
- I can measure data quality in term of completeness
  - If my data are not complete either I produce them or buy them
- Conformity among databases is also important (same format for same data)
- Consistency: are my data contradicting each other
- Accuracy: how much can I trust the data?
- Uniqueness: do I have duplicates?
- Integrity: are data are linked correctly to each other
- How do I assure that data is correctly mantained?
- Deep learning, contrary to ML, In general does do feature extraction by itself
- Interactomic studies have very low reproducibility for technical reasons
- The coverage of proteomic and interactomic studies is never complete
- Many interactomic studies neglect subcellular localization
- It is also difficult to detect liquid-phase separation clusters in vivo
- When I see a network in STRING I do not now if all the interaction happen in the same subcellular compartment!
- The first account of PPI was in 1905 about trypsin and its regulators
- Interactions documented in the PDB are PPIs and ligand-protein interactions
- About 1/3 of the PDB structures are complexes
- There is not significance difference in the distribution of areas of homo and hetero-interfaces (but homointerfaces tend to be larger)
- The distribution of residuea is similar for homo and hetero interfaces (but Cys tend to be more common in heterointerfaces)
- Note that in X-ray structures not all the interfaces are functional!
  - Some interfaces can only be due to the unit cell configuration
- An interface can be defined as the set of residues that undergo a difference in solvent accessible area of more than $1 \AA^2$ ($\Delta{ASA}$) upon binding (as calculated by DSSP)
- Another definition can be the set of residues whose $C_\alpha$ are at less then $12\AA$ Euclidean distance
- Proteases have a very easily recognizable interaction surface
  - In this way every interacting residue is described by a matrix
- There are not strong residue propensities for interaction interfaces (just a little enrichment in hydrophobic residues)
- Since there are no major emerging features for PPI surfaces, ML is the go-to method
- Casadio's group created the ISPRED series (ISPRED1 to 4) of PPI predictors
  - ISPRED predicts interacting residues from **structure**
  - The last version uses hidden support SVMs and conditional random fields
    - An HMM-SVM is an SVM applied to the output of an HMM
  - The first implementations were based on NN
  - They used DSSP to get residues that are more than 16% exposed, and repesented them only in terms of $C_\alpha$
    - This was done in order to reduce the input space
  - They then created a window around the interacting residues (selecting the 10 closest exposed residues in space at less than 12 nm distance) and built a profile on it (accornding to a MSA)
  - Current accuracy is arounf 0.7 and MCC 0.45
- These predictors can be used as a preliminary operation to docking in order to constrain the docking space
- Note that these predictors do not predict who the interactors are!
- Now they are working on the prediction of interacting residues from sequence
  - Current MCC is 0.3
  - Note that this requires first to predict the solvent accessible area from sequence (which is hard in itself)
- Database of PPI are BioGRID, ComplexPortal, IntAct, MINT, STRING
  - They usually do not agree on the interactions reported!
  - Usually if I need to build an interaction network I want to use the intersection of these databases, so the interactions reported by all of them
- Note that many interaction experiments are done in vitro so I am not sure if the interaction actually happens in cells!
- An interactome is a partial view of reality!
- MINT was in Rome but now it is in Milan

# Part 2 - Prof. Savojardo

## Introduction to the Project

- Here we will extend our practice in functional annotation with a project
- We will compare the GOR method and SVM for the prediction of secondary structure form sequence
- We will be provided with data (fasta sequences and dssp assignments) and CV splits
- We will need to generate a testing set from the PDB database
- We will prepare our data and implement the GOR and SVM predictors
- We will discuss critically the results and write a manuscript
- The manuscript should be compliant with the OUP Bioinformatics journal guidelines

## Virtual Machine Configuration

- All the computationally-intensive tasks will be done in a VM that they will provide
  - The VM has 2 cores, 8 Gb of RAM, 50 Gb of HDD
  - All the software needed will be available in a conda environment
- The VMs will be accessed through a VPN and SSH
- When you close a terminal, you also close all of its child processes
- In order to let computationally-intensive tasks run while disconnected from the VM we will use screen
  - It is possible also to use nohup or at
- Screen is a terminal multiplexer: you can start a screen session and then into it start as many virtual terminals as you want
- Screen sessions are persistent when the terminal that originated them is closed
- A new screen session is created with the command `screen`, which also creates a window inside the session and starts a shell into it
- To detach from the current session I press `Ctrl+a d`
- I can list detached sessions with `screen -ls`
- I can reattach a detached session with `screen -r`
- I can create a new window in the same session with `Ctrl+a c`
- I can list all the windows in the current session with `Ctrl+a "`
- I can show an help with `Ctrl+a ?`

## DSSP

- DSSP is both used to indicate the software and a databae of SS assignments
- DSSP is not a predictor, it uses an algorithm to assign a secondary structure
- It is run with the command `mkdssp`, and by defaults it outputs to STDOUT (I can specify an output file with the `-o` parameter)
- The output is a fixed-width flat-file that can be parsed by extracting substrings

\small

```
HEADER    HYDROLASE   (SERINE PROTEINASE)         17-MAY-76   1EST
...
  240  1  4  4  0 TOTAL NUMBER OF RESIDUES, NUMBER OF CHAINS,
                  NUMBER OF SS-BRIDGES(TOTAL,INTRACHAIN,INTERCHAIN)                .
 10891.0   ACCESSIBLE SURFACE OF PROTEIN (ANGSTROM**2)
  162 67.5   TOTAL NUMBER OF HYDROGEN BONDS OF TYPE O(I)-->H-N(J)  ; PER 100 RESIDUES
    0  0.0   TOTAL NUMBER OF HYDROGEN BONDS IN     PARALLEL BRIDGES; PER 100 RESIDUES
   84 35.0   TOTAL NUMBER OF HYDROGEN BONDS IN ANTIPARALLEL BRIDGES; PER 100 RESIDUES
...
   26 10.8   TOTAL NUMBER OF HYDROGEN BONDS OF TYPE O(I)-->H-N(I+2)
   30 12.5   TOTAL NUMBER OF HYDROGEN BONDS OF TYPE O(I)-->H-N(I+3)
   10  4.2   TOTAL NUMBER OF HYDROGEN BONDS OF TYPE O(I)-->H-N(I+4)
...
  #  RESIDUE AA STRUCTURE BP1 BP2  ACC   N-H-->O  O-->H-N  N-H-->O  O-->H-N
    2   17   V  B 3   +A  182   0A   8  180,-2.5 180,-1.9   1,-0.2 134,-0.1
                                   ...Next two lines wrapped as a pair...
                                    TCO  KAPPA ALPHA  PHI   PSI    X-CA   Y-CA   Z-CA
                                  -0.776 360.0   8.1 -84.5 125.5  -14.7   34.4   34.8
                                   ...Next two lines wrapped as a pair...
                                               CHAIN AUTHCHAIN
                                                   A         A
....;....1....;....2....;....3....;....4....;....5....;....6....;....7..
    .-- sequential resnumber, including chain breaks as extra residues
    |    .-- original PDB resname, not nec. sequential, may contain letters
    |    | .-- one-letter chain ID, if any
    |    | | .-- amino acid sequence in one letter code
    |    | | |  .-- secondary structure summary based on columns 19-38
    |    | | |  | xxxxxxxxxxxxxxxxxxxx recommend columns for secstruc details
    |    | | |  | .-- 3-turns/helix
    |    | | |  | |.-- 4-turns/helix
    |    | | |  | ||.-- 5-turns/helix
    |    | | |  | |||.-- geometrical bend
    |    | | |  | ||||.-- chirality
    |    | | |  | |||||.-- beta bridge label
    |    | | |  | ||||||.-- beta bridge label
    |    | | |  | |||||||   .-- beta bridge partner resnum
    |    | | |  | |||||||   |   .-- beta bridge partner resnum
    |    | | |  | |||||||   |   |.-- beta sheet label
    |    | | |  | |||||||   |   ||   .-- solvent accessibility
    |    | | |  | |||||||   |   ||   |
  #  RESIDUE AA STRUCTURE BP1 BP2  ACC
    |    | | |  | |||||||   |   ||   |
   35   47 A I  E     +     0   0    2
   36   48 A R  E >  S- K   0  39C  97
   37   49 A Q  T 3  S+     0   0   86
   38   50 A N  T 3  S+     0   0   34
   39   51 A W  E <   -KL  36  98C   6
```

\normalsize

- The first column contains an internal residue identifier (different from the PDB one)
  - It contains `!` when a chain break is detected by dssp itself (because 2 successive $C_\alpha$ are too far from each other)
  - It contains `!*` when there is a chin break in the PDB file
- DSSP produces 8 different SS types, that then are usually reduced to H, E and C (externally to dssp)
- Typical mapping is
  - H, G, I $\to$ H
  - B, E $\to$ E (sometimes B is mapped to C to avoid short strands)
  - T, S, " " $\to$ C
- The last column is the absolute solvent accessibility
  - Note that the calculation ignores HETATM and unusual residues, so I can get unexpectedly large valuues when these are present
  - If I have an oligomer the accessibility is returned for the entire assembly, so it neglects the interaction surface!
    - Extract the chains first if you want the accessibility of the monomer
- Residues in a disulphide bridge are reported with the same lowercase letter

## Dataset

- Our dataset was the one used for training Jpred4, one of the most recent SS prediction methods
- The starting set contained 1987 representative domain sequences from each 2.04 SCOP superfamily
  - They did like this to exclude obvios sequence similarities
- They filtered out the set to 1497 proteins by removing
  - Proteins with a structure worse than $2.5 \AA$
  - Sequences shorter than 30 residues (they cannot contain a domain) or longer than 800 (to avoid long Blast runs)
  - Missing dssp assignments for more than 9 residues consecutively
  - Other filters
- They split the dataset in a training set (1348 sequences) and a blind test set (149 sequences)
- We will use only the train split, and we will build our own test set
- We will need to produce some statistics on the dataset in the paper

## Data Visualization

- Barplots are used for visualizing a quantitative and a qualitative variable
- Histograms are used with 1 quantitative variable discretized in bins
  - The dependent variable is the frequency of each bin
  - The size of the bin is essential for good visualization
- Density plots are similar to histograms but do not use bins
  - They use kernel smoothing for plotting probability densities
  - They are better than histograms since they are not influenced by bin size
  - A gaussian kernel interpolates a series of gaussians centered into each datapoint
- Heatmaps visualize trivariate data with 2 independent variables

---

# To integrate

## Secondary Structure

- Secondary structures are local motives of order
- JCE has been removed from the PDB website
- I can use TopMatch for pairwise structural alignment, and Mustang for multiple structural alignment
- H is usually not visible in 3D structures, since it needs a resolution better than 1 $\AA$
- Molecular visualization softwares in order to show secondary structure use algorithms that compute the position of hydrogens
  - Jahnet Tornhton developped one of the most used algorithms
- A protein is a stable entity when there is the right combination of residues that allow the backbone to fold in the solvent space
- An hydrogen bond is on average $2 \AA$ long
- The atoms involved in the H bonding should be strongly electronegative
  - The H is in a frustrated, unstable position
- In an alpha-helix H bonds occur with the 4th following residue
- H-bonding happens both in solvent-accessible and solvent-unaccessible regions
- Protein with the same secondary structure topology are probably similar also in tertiary structure
  - This is in spite of primary structure
- HMMs can be used to model domains, not entire proteins
- Comparing protein topology allows to predict the structure of entire proteins
- If you are lost for a protein, predict its secondary structure and allign it against the PDB filtered so to apper as a set of secondary structures
- The accuracy of secondary structure predictors is around 80-90%
  - According to Rost this accuracy is an upper limit, given the resolution of the atomic coordinates of proteins
- An helix is at least 4 residues long, while a strand is at least 2 residues long
- There is no upper limit, but there are helices in fibers which are several hundred residues long
- The topology is the organization in space of all the secondary structure motives of a protein
  - For our purpose it is all the different patterns of secondary structure from the N to C terminus
- When using a sliding window, the central residue of the window is assigned the average value of the entire window
  - This causes a smoothing of the values across a sequence
- Local features are better grapsed by sliding windows
- HMMs are not suitable for modelling local features like secondary structures
- Chamelion segments are combinations of residues that can be found in different secondary structures

## Protein Stability

- A genetic variant of a protein (an allele with a single aminoacid difference) can have a different stability than the original protein allele
- A variation in $\Delta G$ among 2 proteins due to a genetic variant, called $\Delta \Delta G$ can increase or decrease protein stability
  $$ \Delta \Delta G = \Delta G*{mut}-\Delta G*{nat}$$
  - If $\Delta \Delta G > 1.0$ the variation increases protein stability
    - If $\Delta \Delta G < -1.0$ the variation decreases protein stability
    - If $\Delta \Delta G < -1.0$ the variation decreases protein stability
    - If $1.0 < \Delta \Delta G < 1.0$ the variation has little effect on protien stability

## Hydrogens in Macromolecular Models

- See [**this proteopedia link**](https://proteopedia.org/wiki/index.php/Hydrogen_in_macromolecular_models) for details
- Approximately 50% or protein atoms and 35% of nucleic acids atoms are hydrogens
- Most crystals do not have sufficient resolution (1.0 Ångstroms or better is needed) to determine the positions of hydrogen atoms directly
- It is easy to add hydrogens to macromolecular models, but the results are only as good as the molecular models themselves
- High resolution protein crystallography (1.2 Ångstroms or better) can assign some hydrogen positions empirically from the electron density map, and very high resolution crystals (1.0 Ångstroms or better) can assign the positions of most hydrogens
- It is easy to add hydrogens to macromolecular models (PDB files) using the highly-reliable free servers MolProbity and WHATIF

## Uniprot

- Annotation in UniProt is manual and automatic
- SwissPort includes only manually reviewed proteis, despite their annotation quality
- Automatic annotation is based on UniRule and SAAS
- UniRule rules are made by expert curators, while SAAS rules are automatically generated
- SAAS uses machine learning to create rules from analysing manually and UniRule annotated entries

## DSSP

- DSSP is an algorithm developped by Sander and Kabasch in 1983 for the assignment of secondary structure to 3D structures
  - First hydrogens are added according to the chemical properties of elements
  - Then DSSP uses a purely electrostatic definition to assign hydrogen bonding patterns and, from this, secondary structure
- The DSS algorithm is embedded in many visualization softwares
- The goal of DSSP is to approximate the intuitive concept of secondary structure with an objective algorithm
- Extracting structural features from a set of coordinates is a pattern recognition process
- Using torsion angles for assessing secondary structure requires many parameters, while using the presence of hydrogen bonds requires a single parameter: bond lenght
  - Torsion angles are defined using the position of 4 atoms each
- n-turns are defined by the presence of an H-bind between the CO of residue $i$ and the NH of residue $i+n$, with $n=3,4,5$
- Bridges are defined similarly to turns, but for $n>5$
- Bridges are also required to be at least 3 residues long
- Alpha helices are described by repeating 4-turns, while beta structures are defined by repeating bridges
- A series of 3-turns describes a 3:10 helix, while a series of 5-turns describes a $\pi$ helix
- Other structures such as 3-10 helices, $\pi$ helices, single turns, and single beta bridges are derived from combinations of these fundamental elements
- Bends, chirality, and solvent exposure are defined geometrically
- Each feature is assigned independently and structural overlaps are resolved by defining a summary that assigns a single state to each residue
- H bonds in proteins have little wave-function overlap and can be descrobed with purely electrostatic terms
- Partial charges are placed in the H bonding groups
  - C is assigned +0.42 eV, O -0.42 eV
  - N is assigned -0.20 eV, H +0.20 eV
- The electrostatic interaction is then calculated as
  $$E = q_1q_2(\frac{1}{r_{ON}}+\frac{1}{r_{CH}}-\frac{1}{r_{OH}}-\frac{1}{r_{CN}})*f$$
- A good H bond as an energy of -3 kcal/mol, but the cutoff used is -0.5 kcal/mol to account for errors in coordinates and bifurcated bonds
- There is no universally accepted H bond definition, so a description is necessarily tailored to a purpose
  - Their definition demonstrated to be adequate for the purpose
- Imperfections in helices are allowed in order to account for kinks
- Bends are assigned to regions with a curvature of more than 70° along 5 consecutive residues
  - The bend is assigned to the central of 5 residues
- Chirality is defined at each residue (except chain ends) as the sign of the dihedral angle among 4 consecutive Ca
- SS bonds are taken directly from the PDB record, since they can be considered part of the primary structure
- Chain breaks are assumed for peptide bonds longer than 2.5 $\AA$
- Structural overlaps are resolved with a priority rule
- Each secondary structure is assigned a code, that is also used in many applications outside of DSSP
  - G is a 3:10 helix of at least 3 residues
  - H is an alpha helix of at least 4 residues
  - I is an $\pi$ helix of at least 5 residues
  - T is a turn (3,4, or 5 turn)
  - E is an extended strand (parallel or antiparallel) in beta conformation, at least 2 residues long
  - B is an isolated bridge of 1 residue
  - S is a bend, assigned not according to H bonds but to geometry
  - C is a coil, a residue in none of the above conformations
  - Other categories exist, but are rarely used
- DSSP is generally accepted as a tool for assigning secondary structure
- I can get solvent exposure values that are higher than expected when heteroatoms are present, since they are ignored
- I can get solvent exposure values that are lower than expected when oligomers are present, since the exposure is calculated for the oligomer and not for the monomer

## LB2 Project

- We will compare 2 different approaches for predicting protein secondary structure
  - The GOR method, based on statistical analysis
  - Using SVM (background from Martelli)
- We will be given the training data and the cross-validation splits
- Training data are FASTA files and DSSP secondary structures
- We will implement everything in python
- They will provide us a virtual machine with linux with 8 Gb RAM and 50 Gb HDD, with all the necessary software installed in conda

## Neural Networks

- McCulloch e Pitts (1943) modeled a neuron as an object receiving an input vector and producing a scalar output via linar combination of the inputs (with weights), transformed by a transfer function
- A simple perceptron has just an input layer and an output layer, and operates only in a feed-forward manner
- A multi-layer perceptron contain hidden layers of neurons
- A NN is an alternative computational paradigm in which the solution to a problem is automatically learned from a set of examples
- A NN performs general non-linear mapping
- A single-layer perceptron performs a total summation of the inputs $x_i$, each associated with a weight $w_i$, in order to determine the activation $a$, and the output $z$ after applying the transfer function $g(a)$
  $$a=\sum_i w_i x_i$$
  $$z = g(a)$$
  - The bias of the neuron is usually represented as an additional input $x_0$
- The error function of the perceptron is proportional to the sum of squared differences between predicted and real values, over all the training examples and over all the output neurons
- For the single training point $X^q$, if $D_i^q$ is the real desired value of example $q$ for output neuron $i$
  $$ E^q = \frac{1}{2} \sum_i (Y_i(X^q)-D_i^q)^2$$
- The NN reaches an optimal configuration when its error function is minimal

## Protein Phase Separation

sdfsdfsdf (Hello world)

$\pi \mu$
