% Laboratory of Bioinformatics 2
% Saul Pierotti
% \today

# Random
* JCE has been removed from the PDB website
* I can use TopMatch for pairwise structural alignment, and Mustang for multiple structural alignment
* Molecular visualization softwares in order to show secondary structure use algorithms that compute the position of hydrogens
	* Jahnet Tornhton developped one of the most used algorithms
	* DSSP is another algorithm developped by Sander and Kabasch
	* First hydrogens are added according to the chemical properties of elements
	* DSSP uses a purely electrostatic definition to assign hydrogen bonding patterns and, from this, secondary structure
* A protein is a stable entity when there is the right combination of residues that allow the backbone to fold in the solvent space
* An hydrogen bond is on average $2 \AA$ long
* The atoms involved in the H bonding should be strongly electronegative
	* The H is in a frustrated, unstable position
* In an alpha-helix H bonds occur with the 4th following residue
* H-bonding happens both in solvent-accessible and solvent-unaccessible regions
* Protein with the same secondary structure topology are probably similar also in tertiary structure
	* This is in spite of primary structure
* A genetic variant of a protein (an allele with a single aminoacid difference) can have a different stability than the original protein allele
* A variation in $\Delta G$ among 2 proteins due to a genetic variant, called $\Delta \Delta G$ can increase or decrease protein stability
	* If $\Delta \Delta G > 1.0$ the variation increases protein stability
	* If $\Delta \Delta G < -1.0$ the variation decreases protein stability
	* If $\Delta \Delta G < -1.0$ the variation decreases protein stability
	* If $1.0 < \Delta \Delta G < 1.0$ the variation has little effect on protien stability
* HMMs can be used to model domains, not entire proteins
* Comparing protein topology allows to predict the structure of entire proteins
* If you are lost for a protein, predict its secondary structure and allign it against the PDB filtered so to apper as a set of secondary structures
* The accuracy of secondary structure predictors is around 80-90%
	* According to Rost this accuracy is an upper limit, given the resolution of the atomic coordinates of proteins
* The topology is the organization in space of all the secondary structure motives of a protein
	* For our purpose it is all the different patterns of secondary structure from the N to C terminus
* The DSS algorithm is embedded in many visualization softwares
* An helix is at least 4 residues long, while a strand is at least 2 residues long
* There is no upper limit, but there are helices in fibers which are several hundred residues long

# LB2 Project
* We will compare 2 different approaches for predicting protein secondary structure
	* The GOR method, based on statistical analysis
	* Using SVM (background from Martelli)
* We will be given the training data and the cross-validation splits
* Training data are FASTA files and DSSP secondary structures
* We will implement everything in python
* They will provide us a virtual machine with linux with 8 Gb RAM and 50 Gb HDD, with all the necessary software installed in conda
