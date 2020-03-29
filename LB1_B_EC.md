% Laboratory of Bioinformatics 1 part B - Capriotti
% Saul Pierotti
% \today

# Introduction
* There will be a project for the final, to be submitted for May 18
* Protein structure is more conserved than sequence
* When sequence identity is sufficiently high, we can tranfer structural information
* A structural alignment is a rigid body transformation of 2 subsets from 2 sets of points that maximizes a given distance metric
	* The subsets need to have the same number of elements and define the corrispondence set
	* Finding the corrispondece set is an NP-hard problem
	* Finding the optimal rigid transformation of the corrispondence set is $\Theta(n)$
* The distance of 2 sequences can be evaluated with a substitution matrix and a gap penalty
* Global alignments are computed with the NW algorithm, local alignments with the SW
* Local alignments are useful for multidomain proteins, when only some domains are conserved
* The significance of an alignment score can be evaluated by comparing with the score distribution for random alignments
* Sanders and Schneider developed a twilight curve before Rost
	* Sander's curve becomes straight after 80 residues
	* Rost's curve does never become straight
* Over 100 residues, under 25% of sequence identity only 10% of the sequences are homologous, while above 20% 90% of them are
* Over 30% identity sequences longer than 100 residues have similar structures, but this does NOT mean that under 30% the structure is necessarily different!
* Proteins with low sequence identity but high structural similarity are referred to as remote homologs
* Structures can be predicted by comparative modeling, threading, ab initio
* If I want to use sequence identity for trasferring annotation features, I need to identify the problem-specific twilight region
	* For subcellularlocalization, the twilight zone is 50% (!)
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
* The expected score or random pairwise alignments is an extreme value distribution
	* I would have a gaussian if there was no evolution
	* In real databases I have an excess of good-scoring pairs
* When I want to determine the distribution of scores, it is better to have an analitycal distribution than an empirical one
	* I don't have tools for working with empirical distributions (!)

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
* Secondary structure of RNAs is usually represented with parenteses
	* I cannot represent pseudo-knots in this way
* For RNA, the secondary strucutre is much more informative than for proteins
	* A certain secondary structure constraints a lot the tertiary structure
* There is less variability in RNA strucutures than in proteins
* The best atom for representing the backbone is C3', since it has the most constant inter-nuclotide distance
* The professor adapted MAMMOTH to work with RNA C3' atoms instead of Ca in proteins: SARA
	* The statistics of the score had to be re-evaluated
	* They still used the extreme value distribution, which is defined by $\mu$ and $\sigma$
	* They selected how the parameters change when RNA size changes
	* The set of unit vectors was 3 instead of 7 
	* The method gives a -log(p-value) score
	* By comparing RNAs of known function, I can determine a score threshold that gives correct functional annotation
* Another method was developped in Israel: ARTS
* Few people are working in RNA: not so many methods
* The twilight zone of RNA sequence alignment is around 60%
* Secondary structure identity (PSS) correlates well with tertiary structure identity (PSI) but not with sequence identity

# Multiple sequence alignment
* In MSA it is easier that in pariwise alignments to identify conserved regions, that could be functionally important
	* We can observe blocks of conservation in MSAs
* I can transform a MSA in a profile of the sequences
* A profile is a matrix with a row for each possible residue and a column for each position
	* The value of each element reflects the frequency of a residue in a specific position
	* Each position is therefore a vector of 20 elements
	* I represent a profile as a matrix containing as many vectors as the number of positions
	* I can also have a row for the presence of a gap in the position
* A sequence logo is a plot showing the entropy of each residue in each position
	* It is obtained from a profile and it is a way to represent it
* Shannon entropy: information content of a message
	* For a single colum $S(p) = \sum_{i=1}^{20}-p_i \ln{p_i}$
	* Total conservation: $S(p)=0$
	* All residues are equally probable: $S(p)=ln(20)$
	* There are more sofisticated models that take into account the expected frequency of residues
	* The entropy of an alignment is obtained by summing the Shannon entropy over the all alignment
* Scoring an MSA: sum of pairwise scores or entropy score
	* Not all the position are equal in an MSA: some conservations are critical, others not
	* Scoring has necessarily to depend on the evolutionary history of the sequences
	* Almost all scoring functions assume positional independence
* I can score each pairwise alignment and sum it
	* $S = \sum_{i<j} S(A_i,A_j)$
* I can score an MSA depending on its entropy
	* The best alignment is the one with the lowest entropy (i.e. the most conserved one)
	* It is the sum over the alignment of the entropy in each position
	* $S = \sum_{j=1}^{N cols}\sum_{i=1}^{20}-p_i \ln{p_i}$
* I can align a sequence to a profile
	* Each position is aligned to a vector for the position
	* The score for the position of the residue in the sequence with every possible residue is summed and weighted for the frequency encoded in the vector
		* This is a matrix by vector multiplication (!)
	* These scores can be used with a dynamic programming algortihm

# Algorithms for MSAs
* Dynamic programming approaches exist, but they are $O(N^M)$ and they are np-hard
* An MSA method can be evaluated from the functionally important residues that are correctly aligned

## Progressive MSA
* ClustalW is an example of progressive MSA
* I allign sequences in pairs, one after the other
* The result depends on the order of how I pair sequences (!)
	* I usually pair the most similar sequences first
* Similarity is measured by Kimura distance (see MUSCLE for more info)
* From each pairwise alignment, I build a profile
* I iterate until there are no sequences left, by aligning pairwise sequences and profiles
* In order to do this I need to be able to align profiles (!)
* I want to be conservative with gaps with the initial pairwise alignments, and introduce them later on profiles
	* When I get to profiles I have info about conservation (!)
	* Errors in the first alignments are propagated
	* If I am not conservative I can become full of gaps
* I can improve the alignment by changing the sequence tree
	* By default Clustal uses NJ
	* Maybe I have a tree available (!)
* Adding gaps is tricky, since their penalty logically depends on the position and conservation
	* They are usually added in the fisrt alignments
* In ClustalW the penalty is multiplied by a factor which is context specific
	* Gaps in hydrophobic regions are more penalised
	* These coefficients were derived from gaps frequencies in a large number of structural alignments
	* Gaps are discouraged if there is another gap nearby in the MSA
* Low-scoring alignments are postponed for later by adjusting the tree
	* ClustalW aligns them when it has more information deriving from the profiles
* A profile-to-profile alignments involve the pairwise comparison of same-dimentional vectors
	* I do a double sum all against all elements weighted with a substitution matrix
	* This is done via a simple vector to matrix multiplication, followed by a multiplicatio for the remaining vector (!)
* ClustalW corrects for biased representation of subfamilies
* The scoring matrices used change depending on the similarity of the sequences to be compared
* In general, ClustalW uses an heavily crafted heuristics
* The main problem of progressive alignment: subalignments are frozen in place
	* Once aligned, a group of sequences cannot be re-aligned by taking advantage of the new information deriving from other sequences

## Iterative MSA
* Iterative MSA tries to overcome the problem of frozen subalignments
* MUSCLE: multiple sequence comparison by log expectations
* It is based on 3 steps: draft progressive, improved progressive, and refinement
* Draft progressive: create a first progressive MSA
	* Sequence similarity is defined by k-mer distance, not pairwise alignment score
		* If a rare kmer is present in 2 sequences maybe they are related
	* It creates a distance matrix with all sequences against each other
	* It uses UPGMA instead of NJ for building the tree from the matrix
	* The score is based on log expectations, not pairwise score for profile to profile alignments
		* It is the entropy score
* Improved progressive: from the draft create a new matrix and from that a new tree and a new alignment
	* The pairwise distances are calculated from the Kimura distance
		* $K_{dist} = - \ln{1-D-D^2/5}$, where D is the pairwise identity
* Refinement: cut and re-align the tree
	* I edge is deleted at random from the tree
	* The 2 resulting profiles are re-aligned to each other to get the full MSA
	* If the score improves, keep the new MSA otherwise keep the previous one
	* This is iterated until convergence on a local minimum

## Consistency-based MSA
* Consistency: if residue X is aligned with Y and Y is aligned with Z, then X is aligned to Z
	* This is necessarily true in an MSA
* In reverse, I can use consistency to align two sub-alignments: I take advantage of transitivity of alignments
* MSA are not necessarily consistent with the repsective pairwise alignments
	* Progressive MSA methods frequently are not consistent with the pairwise alignments used for building the tree
* T-Coffe (tree-based consistency objective function for alignment evaluation) is an MSA method based on consistency
	* Build the primary library
		* I do all the possible pairwise alignments and I measure the pairwise sequence identity
		* Each pairwise alignment is equipped with a weight equal to the average identity of matched residues, ignoring gaps
	* Build the extended library
		* In order to align sequences A and B, I try all the possible alignment, direct and based on an intermediate sequence C
		* The weight of each alignment is the minimum of the pairwise weights for the intermediate alignments
		* The final weight of a position is the sum of the weights of all the possible alignments supporting it
	* Maximise the pairwise alignments from the extended library with dynamic programming
		* The score of each match corresponds to its weight
	* From the extended pairwise alignments, build a guide tree
	* Do a progressive MSA from this guide tree and the extended pairwise alignments
	* T-Coffe considers both global and local pairwise alignments and it can use information about domains and motifs

# MSA benchmark
* BaliBASE was the first large-scale benchmark specifically designed for MSA
	* It is a dataset with manually refined alignments derived from structural superimposition
* BaliBASE is subdivided in several reference datasets
	* 1 - Small number of equidistant sequences
		* This is further subdivided by identity levels
	* 2 - Families with one or more orphan sequences
	* 3 - Pair of divergent subfamilies with less than 25% reciprocal identity
	* 4 - Sequences with large extensions at the N or C terminal
	* 5 - Sequences with large internal indels
* The evaluation of the benchmark is based on a series of scores
	* The scores are evaluated only for columns that are reliably aligned in the reference (core columns)
	* Sum of pairs score (SP score): proportion of correctly aligned residue pairs in the core columns
	* Total column score (TC score): proportion of completely correclty aligned core columns
	* TC and SP score both are a number between 0 and 1
	* In a pairwise alignment SP and TC score are necessarily equal
	* In an MSA with 3 or more sequences, SP >= TC
	* Both scores encourage sensitivity, but they do not test for specificity
		* There is no penalty for wrong alignments (!)
* BaliBASE also evaluates time of execution and peak memory usage
* SP, TC, memory and time are reported as Z-scores on a spiderweb plot for each alignment tool
* What comes out of the BaliBASE benchmark?
	* No single method is perfect in all cases (!)
	* On average, consistency-based methods are more accurate but slower
	* T-Coffe suffers with N and C terminal extension
	* ClustalW and MUSCLE are the least resource-heavy tools
	* T-Coffe and MAFFT are well suited for alignments larger that those in BaliBASE
	* Multi-threading can greatly speed-up these softwares, since there is a lot of parallel computing
	* Many algos take advantage of parallel processing

# Probabilistic models of protein families
* I can define the probability of a sequence $s_i$ to be generated by a family described by the model $M$
	* $p(s_i|M)$
* I want my model to be trainable and consist in a probability density function
	* A basic model can be based on a similarity measure of the sequence to the family
* What I really want is not $p(s_i|M)$ but $p(M|s_i)$
	* This is the probability of the model given the sequence
	* My given is always the sequence (!)
* To pass among the 2 I need Bayes theorem and so $p(M)$ and $p(s_i)$
* $p(M)$ can be estimated from the abundance of the family (number of sequences contained)
	* A family with many sequences is a priori more probable to contain any sequence
* I cannot exstimate $p(s_i)$!
* I can overcome this by comparing different models
	* The ratio of conditional probabilities of the sequence on 2 models allows to cancel the $p(s_i)$ term
* To standardize the calculation for all families, we can create a null model
* The null model can equiprobably generate any sequence and it takes into account only differential residue probabilities
* A Markov chain is the probability of a sequence of events that depend only on the event before
	* It is given by the probability of the first event of the chain times the chain of conditional probabilities (transition probabilities)
* I can apply a MM to the probability of sequences
	* I can model the probability of a residue given the one before
	* Since I have also BEGIN and END states the MM has N*(N+2) parameters
	* For the model to be complete the sum of probabilities going out of a node has to be 1
