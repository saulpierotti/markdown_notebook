% Laboratory of Bioinformatics 1 part B - Capriotti
% Saul Pierotti
% \today

# Introduction
* There will be a project for the final, to be submitted for may 18
* Protein structure is more conserved than sequence
* When sequence identity is sufficiently high, we can tranfer structural information
* A structural alignment is a rigid body transformation of 2 subsets from 2 sets of points that maximizes a given distance metric
	* The subsets need to have the same number of elements and define the corrispondence set
	* Finding the corrispondece set is an NP-hard problem
	* Finding the optimal rigid transformation of the corrispondence set is $\Theta(n)$
* The distance of 2 sequences can be evaluated with a substitution matrix and a gap penalty
* Global alignments are computed with the NW algorithm, local alignments with the SW
* The significance of an alignment score can be evaluated by comparing with the score distribution for random alignments
* Over 100 residues, under 25% of sequence identity only 10% of the sequences are homologous, while above 20% 90% of them are
* Over 30% idnetity sequences longer than 100 residues have similar structures, but this does NOT mean that under 30% the structure is necessarily different!
* Proteins with low sequence identity but high structural similarity are referred to as remote homologs
* Structures can be predicted by comparative modeling, threading, ab initio
* If I want to use sequence identity for trasferring annotation features, I need to identify the problem-specific twilight region
* The sequence identity needed for transferring subcellular localization is higher than that required for structure
* Function of proteins with really high sequence identity can be completely different
* In remote homologs the sequence alignment is often wrong
* Important residues in a sequence can be identified by comparing conservation levels

# Structural alignment
* Structural alignment is different from superimposition
* Superimposition assumes that I already have the correspondence set, and it is relatively easy
* Structural alignment requires the identification of the correspondence set, which is hard
* The definition of domain is often heuristic and questionable
* Proteins with similar spatial distribution but different topology are difficult to align
* Alignment methods can be classified in different ways
	* Pairwise or multiple
	* Depending on the descriptor used
		* Backbone
		* All atoms
		* Sequence-based
		* Contact map
		* Surface
	* Rigid body or flexible
* The comparison of torsion angles is $\Theta(n)$
	* They are invariant for rotation and translation
	* It is good for local regions but problematic for whole structures
* A distance matrix is also invariant for rotaion and translation
	* Comparing matrices is hard, $\Theta(n^2)$
	* It is not sensitive to chirality
* At the moment, all methods are able to identify obvious similarities
* Remote similarities are detected by a subset of methods, and different methods recognize different similarities
* Speed is an issue in many algorithms
* We want our method to be biologically meaningful, not only geometrically

## CE algorthm
* Compares AFPs composed of 8 residues, stiches them together and finds an optimal path trough them with dynamic programming
* It gives a statistical score
* The alignment is the longest continuous path of AFPs in a similarity matrix S
* The similarity matrix S is composed represent all AFPs conforming to a similaritt criterion
* The dimensions of S are (na-m)(nb-m), where na and nb are the length of the sequences and m the size of the AFPs
* The matrix is large to compute, therefore we need constraints
* Two consecutive AFPs can be aligned with a gap in protein A, a gap in protein B or without gaps
* The AFP lenght is set to 6 and the maximum possible gap to 30
* Similarity measures are RMSD, full set of distances, and others
* The best 20 alignments with Z score above 3.5 are compared based on RMSD and the best one is kept
	* I get an error in 1000 comparisons
* Each gap is assessed for relocation up to m/2 times
* Iteritive optimization with dynamic programming
* It cannot find non-topological alignments
* The unit of comparison was originally the protein chain, but domains are optimal
	* Domains are difficult to define (!)
* The statistical distribution of alignment scores can be used to evaluate the Z score of an alignment

## PDBe Fold
* It uses secondarys structure elements (SSEs)
* Secondary structure is typically conserved
* SSE are represented as vectors that connected in a graph by edges
	* 2 vertices and an edge describe position and orientation of the SSEs
	* SSEs are helices and strands
* Each edge is labelled by a property vector containing information on edge-vertices angles, torsion angles between vertices, lenght of the edge
* The set of vertices, edges and labels defines the graph that is then matched with an algorthm
* Vertex and edge lenghts are compare both in absolute and relative terms
	* In relative terms, the same absolute difference is less significative for longer edges
* Torsion angles are used for distinguishing mirror simmetries
* The SSE matching gives correspondences among SSEs, and can be used to yeld an initial sequence alignment
* Connectivity (topology) can be neglected, considered but allow for any number of missing SSEs (soft connectivity) or allow only for an equal number of unmatched SSEs (strict connectivity)

## MAMMOTH algorithm
* Matching molecular models obtained from theory (MAMMOTH) is one of the fastest algorithms
* The protein is represented as a set of unit vectors among Ca
* It is based on dynamic programming
* An unit vector is the normalized vector among Ca atoms
	* For each position, k consecutive vectors are mapped into a unit sphere that represents the local structure of k residues
* Each set of unit vectors is compare to all the sets in the other structure, building a matrix
* Each comparison yelds a unit root mean square distance (URMS)
	* This is compared against the expected random URMS
	* THe alignment score is obtained by normalizing the URMS with its expected value
* The path trough the matrix is found with dynamic programming by a global alignment without end-gap penalties

# RNA structure
* Most RNAs are around 50 bp
* The best atoms for representing the backbone are C4 and O3, since they have the most constant inter-nuclotide distance
* The twilight zone of RNA sequence alignment is around 60%
* Secondary structure identity (PSS) correlates well with tertiary structure identity (PSI)
