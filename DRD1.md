# DNA and RNA dynamics - part 1

## Introduction
* Professor works in human aging
* Module 1 has a written test, module 2 a report (of course)
* Final score is 20 (module 1) + 10 (module 2)
* Experimental questions should be focused
* Again omics
* In an experiment I have to consider experimental and biological variability
* We can find nucleosomes in blood deriving from apoptotic bodies
	* They are found in microvescicoles
	* Sometimes they can also be free and in this case they are dangerous
* In the lab of prof. Capri they tryed to see if the nucleosome-associated DNA in blood is different in young, old people and centenarians
	* They work a lot with centenarians and they are so proud of it
* We have about 28 millions CpGs in our genome
* CpG metilating/demetilating enzymes: TET (Ten Eleven Translocation), DNMTs
* CpG metilation happens at position 5 of C
* Histone modifications: metilation, acetilation, posphorylation
	* H3k4me3: active promoters
* High expression is associated with high gene metilation and low promoter metilation
	* The causality is not so clear
* The metaorganism: nDNA, mtDNA, microbiome
	* Microbiome influences our phenotype
* RNA are of many types
	* lncRNAs are longer than 200 nt
	* sncRNAs are shorter than 35 nt
	* Middle-sized RNAs
		* Structural: tRNA, rRNA, snRNA, snoRNA
		* Regulatory: ncRNA, siRNA, miRNA, piRNA
* Micro RNAs: pair with mRNA in an inextact way and block translation
	* 18-25 nt
	* They can have many targets
	* They regulate 60% of the mRNAs
	* Each locus can produce 2 miRNAs (5p and 3p)
	* They are in intergenic regions or in introns or also exons!
	* pri-miRNA transcribed by RNA-Pol2
	* Cut by the microprocessor (Drosha/DGCR8) to pre-miRNA
	* pre-miRNA exproted from the nucleus by exportin 5
	* Dicer/TRBP trims it to a miRNA duplex
	* The duplex is separated
	* One miRNA takes part in the RISC complex and it silences mRNAs
	* miRNAs can be found in vescicles/exosomes and go around the body
		* They can act in different cells than the ones that produced them!
* Astronauts could be ageing faster
	* They want to check their DNA associated with nucleosomes before going, after landing and after a while after landing
* I should do technical replicates
* Coefficient of variability: (SD/mean)*100
* The normal distribution
* Biological variability: usually a lot
* I can distinguish biological and experimental variability by carefully designing my experiment
* Box plot: look at data distribution
	* The central line is the median (quartile Q2)
	* The sides of the box are the quartiles Q1 and Q3
	* The lines are 1.5*IQR above/below Q1/Q3
	* Interquartile range (IQR) is Q3-Q1
	* Outliers outside of the lines are shown

## Microarrays
* Tiling arrays cover an entire genome
* I can also have protein arrays
* For transcriptomics and DNA metilation I can use competitive or non competitive arrays
* Production technologies
	* Oligos can be separately synthesised and spotted
	* DNA can be synthesized directly on the chip (GeneChip)
	* Oligos can be separately synthesized and loaded on beads, which are then immobilised on the chip (beadChips)

### Competitive microarrays
* They use 2 colors in the same chip
* Invented 20 years ago at Stanford
* Chip surface coated with aminosilane for binding oligos
* Oligo binding is possible after UV exposure
* Tipycally used with RNA
	* I do retrotranscription using Cy3(green)/Cy5(red) marked nucleotides
* Ibridisation is usually overnight, then I scan the array and acquire the image
* Cy3 and 5 are N-hydroxi-succimidyl esters but Cy5 is bigger
	* Possible bias during retrotrascription!
	* To reverse this, I can retrotrascribe both samples with aminoallyl-dUTP and then couple the dyes via chemical reaction
* ScanArray scans at 550nm for exciting Cy3 and at 649nm for Cy5
	* Fluorescence is measured by PMT
	* Each pixel is a point of measure
	* It uses false colors
* I can address bias by swapping the dyes
* Background fluorescence can be a problem
	* The software filters it out but pixel with luminosity lower than the fluorescence are lost
* For each spot I have a pixel distribution
	* I can get the mean signal, SD, median, median absolute deviation (MAD)
* The row data intensity is typically transformed in log_2 scale
* The MA plot is useful for evaluating the distribution of data in a competitive array
	* The x is the log average intensity (log(Cy3)+log(Cy5))/2)
	* The y is log Cy3/Cy5 ratio
	* It allows to see if the fold change is due to the intensity
* If the MA plot is not horizontal I need to normalise my data
	* Linear normalisation: I can assume that the fluorescence of one of the dyes is related to that of the other by a correction factor k
	* This corrects for different absolute intensities of the dyes
	* I just scale M (the y) by subtracting the log2 of the constant k
	* I can center the M to 0 by using c=log2k=median(M)
* Normalising between arrays: use the same reference sample!
	* Centering: just subtract from M the mean in log space so you center to 0 and divide by SD so that SDnew=1
		* I can also center on the median and MAD
		* It is preferable to use the median when there are outliers (it is less sensitive to outliers)
	* Normalisation: make distributions identical
		* First I need to center the data
		* I compute a reference distribution with lowest value the average of the lowest values of each array
			* I repeat this fo the second lowest and so on
		* I replace each measurement with the corresponding average
			* The highest measurement is replaced with the higest value of the reference distribution and so on
* Coefficient of variability: VAR/mean*100
* The MIAME standard is used for uniformating microarray experiments and allowing comparisons
* Image scanning is crucial for data quality
	* Low laser intensity for reducng photobleach
	* The photomultiplier shuold be set so to balance the Cy3 abd Cy5 channels
* Segmentation is the process of identifying clusters in the image
	* It is done with algoriths and manual inspection
	* There is also an experimental approach that uses DAPI to color the clusters
* Softwares also separate the image in background and foreground (the actual signal)
	* The difference of foreground and background intensities is the spot intensity
* Spot intensities for Cy3 and Cy5 can be use for estimating the overall expression ratio

## Non competitive arrays

### Affimetrix Genechip
* Affimetrix Genechips is a closed platform (only usable with reagents and instruments supplied by them)
* The new form of this kind of chips is called Next generation arrays
* The chemistry was invented in 1991 by Stephen Fodor
* Affimetrix started in California as a startup and then it was acquired by Thermo Fisher
* This arrays are produced by photolotography chemistry
	* It is used for in situ synthesis of oligos!
	* A UV sensitive reaction blocker is selsectively degraded by UV light
* An oligo cluster is called as feature in arrays
* Probes are redundant, in the sense that there are different probes that target different positions of the same mRNA to cross-check and average results
* Mismatch probes: probes similar to normal probes but with a single base mutated in the middle
	* They are used to quantify background and non-specific binding and remove it
	* It is also a control for the actual binding: I expect to have a lower intensity that for the real probe but correlated to it
* There are also complete 8-mer and 9-mer chips!

## Illumina Beadchip (Infinium)
* It uses multi-sample arrays
* The chips contains 3 um pits where beads can be held by VdW interactions
* Each bead is coated with copies of the same oligo
* Optic fibers are connected to each pit, so that they can collect the signal from one bead
* The oligos of the beads contain a 29 nt barcode and a 50 nt target-specific portion
* Illumina Infimium chips are used for methylation studies
* In a single cell for a single position methylation can either be 0%, 50% or 100% in a diploid
* DNA methilation islands have a terminology such as shelf, shore, open sea, north and south (upstrean and downstream) in relation with a real island
* The first chips had 27K probes, more or less one in each CpG island
* Newer ones have 450K probes
* For each island I have a bead for the island, for the shore, the shelf, the open sea
* The newest one, Infinium methilationRPIC, has 850K probes
	* It contains also probes outside CpG islands, non-CpG methylated sites in stem cells, differentially methylated sites in tumors, FANTOM5 enhancers
* Bisulphite conversion: I can deaminate only non-metilated cytosines to uracil
	* The methyl group protects cytosine from deamination
	* Be careful: PCR of course does not reatin methylation patterns!
* Sequencing the DNA before and after bisulphite treatment I can see which sites are methylated by comparing the C/T differences
* Infinium probes have as a last nucletide the one that pairs with the methylated site
* A single-base reation extends the probe using the target sequence
* Labelled nucleotides are used, so that the occurrence of extension can be seen by fluorescence
	* A and T are labeled with DNP
	* C and G are labeled with biotin
	* In the staining phase A/T is colore redwith anti-DNP-red and C/G green with straptavidin-green
* Infinium I assay: 1 color
	* It uses a bead for unmethylated C (U probe) and one for methylated C (M probe)
	* The U probe ends with A (and thus binds T) at the target site, the M probe ends in G
	* U probes can extend only unmethylated sites and vice versa
	* The methylation level (beta-value) is evaluated as the the ratio among M intensity and U+M intensity
		* Usually 100 is added at the denominator to avoid 0/0 cases
	* The color of the signal is not improtant here, just its intensity
	* Since the probe is 50 nt, it can span multiple CpG sites
		* The methilated probe is built with the assumption that all the included sites are methilated (C/G in C of CpG)
		* The unmethilated probe is built with the assumption that all the included sites are not methilated (A/T in the C of CpG)
		* This assumption is reasonable in islands but not so much in the open sea
* Infinium II assay: 2 colors
	* It uses just one bead per site, with the last position just before the target site
	* Nucleotides are differently marked for methylated (C, G) and unmethylated (A, T)
	* The methylation is evaluated in the same way as with Infinum I, but with the instensities coming from different channels of the same bead
	* It does not make any assumption about the state of other CpGs included in the probe
		* It uses degenerate R sites that bind both G and A
		* The all or none approach is not possible since the same probe must bind both methylated and unmethilated sites!
	* Since it uses just 1 bead per site with Infinium II I can include a double number of sites in the array
* Infinium II is less sensitive and more variable
* Beta-values tend to cluster around 0 and 1, but have a continuous (heteroscedastic) distribution
* Another approach is to use M-values: it is the log2 of M/U
	* It is homoscedastic
* Comparing Infinium I and II experiments can be done with intra-array nomalisation
	* I rescale the M-values using the peak summit
	* Corrected M-values are rescaled again to match the Infinium I range
	* At the end these M-values are converted back to beta-values
	* This also reduced variance of Infinium II
* Cytosine methylation can also be studied by bisulphite-WGS (WGBS) or methylated DNA immunoprecipitation (MeDIP)
	* It uses 5mC-specific antibodies
