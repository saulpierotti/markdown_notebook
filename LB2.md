% Laboratory of Bioinformatics 2
% Saul Pierotti
% \today

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

