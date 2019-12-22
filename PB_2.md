% Programming for Bioinformatics
% Saul Pierotti
% \today

# Sequence alignment
* The score of a position can be considered independent from any other position
* It is not always possible to distinguish spurious alignments from true ones
* If we assume independence, the probability of having a string of nucleotides is the product of the probability for each nucleotide in the string
* If we want to be able to sum scores, we need to take the log of the probabilities (!)

# For upload
* We scored an alignment with a blosum matrix stored in a text file

# PAM matrices
* PAM matrices are based on an evolutionary model, while BLOSUM are based on real alignments
* PAM were created by M. Dayhoff in 1972 and their name is an acronim for "point accepted mutation"
* A point accepted mutation is the replacement of a residue by another, which is accepted by natural selection
* The matrix PAMx is a matrix referring to sequences undergoing x PAM every 100 residues
	* Note that this includes multiple mutations at the same site (!)
* The protein set chosen for building PAM matrices had a minumum identity of 85%
* From the set of proteins, they inferred a phylogenetic tree
	* The tree is used to follow all the chain of mutations, also the ones that happened in the same positions
* Higher PAM matrices are computed as powers of PAM1
	* This means that we are using a model, it is not based on observation (!)
* PAM1 is a really stringent matrix: all the values outside the diagonal are really low
* The scores of PAM1 are computed as log_odds of the substitutions

# BLOSUM
* Blosum means block substitution matrix
* They were built by Henikoff and Henikoff in 1992
* They were made by alignments of protein sets with different degrees of conservation
	* We do not assume any model, all the substitutions are based on observed frequencies
* High BLOSUM matrices are used for closely related sequences
