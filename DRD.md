% DNA and RNA dynamics
% Saul Pierotti
% \today

# Introduction
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

# Microarrays
* Tiling arrays cover an entire genome
* I can also have protein arrays
* For transcriptomics and DNA metilation I can use competitive or non competitive arrays
* Production technologies
	* Oligos can be separately synthesised and spotted
	* DNA can be synthesized directly on the chip (GeneChip)
	* Oligos can be separately synthesized and loaded on beads, which are then immobilised on the chip (beadChips)

## Competitive microarrays
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

# Non competitive arrays

## Affimetrix Genechip
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

# Statistical inference
* We do not know the level of population variability from which we draw samples
* Claiming differential expression of a gene means that the expression level of a gene changes systematically between different samples
	* The magnitude of the difference is not relevant
* In experiments I usually want to reject or not the null hypothesis $H_0$
* $\alpha$ is the probability of rejecting $H_0$ when it is true
* $\beta$ is the probability of not rejecting a false $H_0$
* A stringent significance threshold (p-value) increases $\alpha$ and decreases $\beta$
* When I am doing multiple testing I need to restrict the p-value otherwise I get an unacceptably high number of flase positives
* Parametric staistics assumes that the population follows a type of probabilioty distribution
	* That is, it infers parameters of the putative distribution
	* It is usually more powerfull than non-parametric statistics but it makes more assumptions
* Parametric statistics assumes that
	* Measurements are all independent from each other
		* If some measurement are not independent I need to group them in a single variable
	* The measurement are normally distributed
	* The variance is uniform
* An experiment can be designed with paired or unpaired groups
	* A paired group is the same cohort measured before and after a treatment
	* An unpaired group is 2 different cohorts, one to which I gave a treatment and one control
* The t-test is a parametric test which is different for paired and unpaired data
	* I compute a $t$ statistic from the data and I compare it with the appropriate $t$ distribution
	* There is a $t$ distribution for each degree of freedom
	* When $df \to \infty$ the t distribution approximates a normal distribution
	* For lower df the t distribution has fatter tails than the normal distribution
* Paired t-test: $t =\frac{\bar{X}}{\sigma/\sqrt{n}}$
	* It is the mean divided by the standard error of the mean
* The Shapiro-Wilk test returns the p-value for the null hypothesis that the data are normally distributed
	* It should not be significant!
* Unpaired t-test
	* There are 2 different forms, dependig to the fact that the 2 groups have the same variance or not
* Non-parametric method should be used when I have outliers, noisy data, or non-normally distributed data
	* In some cases if I have many measurment it can be difficult to assert normality for all of them
* The Wilcoxon sign-rank test is the non-parametric equivalent of the paired t-test
	* It is based on a ranking of the measuremnts
	* I replace the data with its rank
	* It has a lower power than the paired t-test
* The Mann-Whithney U test (Wilcoxon rank-sum) is the non-parametric equivalent of the unpaired t-test
	* It is also based on ranks
	* I obtain the statistics U and I compare it to a pre-computed distribution

## Bootstrap
* I do resampling with replacement and evaluate the $t$ statistics in each bootstrap
* I produce a distribution of $t$ after thousand of bootstraps

## ANOVA
* It is a generalization of the t test for more than 2 groups

## Kruskal-Wallis test
* It is a non-parametric test that estends the Mann-Whitney U test

## Multiple testing
* Bonferroni correction: just divide by the number of tests
* Benjamin Hunger correction

# Practical part - doctormaragiuliabacalini
* We will prepare a report (:/)
* We will use mainly R
* The CRAN repository has general statistics packages
* Bioconductor is a repository for bioinformatics R packages
* Contributed packages are not always reliable!

## Workspaces, objects, syntax
* Comments are rendered with `#`
* Spaces are ignored except that in variable and function names
* The R workspace contains
* An R object is a variable
	* It cannot contain special characters except for underscore and dot
	* It needs to start with a letter
	* It can be a good idea to always start variables with capital, so to not mix them up with function
	* Objects are assigned with the assignment operator `<-` or `=`
	* In R the operator `<-` is preferred since `=` can be mistaken by `==`
* Data types can be symple or aggregated
* Simple: integer, float, string, boolean, factors, NA (missing data)
* Aggregated: vector (made of numbers or factors), list (made of any datatype), matrix (2 dimensional and numerical), dataframe (2 dimensional and of any type)
* Even a number is actually a vector of lenght 1
* In dataframes columns and rows have names
* A factor is a categorical variable
	* It is like a string but without quotes
	* They can be put in a vector
	* A list of strings can be converted in a vector of factors with `as.factor(list)`
	* The function `levels(vector)` returns the possible categorical values
* In dataframes all the strings are converted to factors
	* This is memory effective since a single categorical variable is represented by just one integer irrespective of its lenght!
* Logical operators
	* Not x `!x`
	* Or `|`
	* And `&`
	* `isTRUE(x)` returns True if the expression x is true
	* `x %in% y` returns true if x is a subset of y
* Indeces
	* A vector is indexed as `v[i]`
	* A matrix or dataframe as `M[i,j]`
* Exploratory functions are particularly useful for dataframes
* Categorical values are ordered alphabetically
* Objects in R can be of various types
	* S3 objects are more casual while S4 objects are more structured
	* An S4 object contains slots, that can be extracted with the operator @
		* Slots are not meant to be accessed by the user
		* Helper functions (`get_something()`) should be used to access the relavant information stored in an object

# Minfi
* Infinium data can be analised with the GUI tool GenomeStudio from Illumina or with one of the many open source R packages
* Minfi is a bioconductor package for Infinium data analysis
	* It uses an S4 indexing structure
* Infinium raw data are in the binary IDAT format (one file per sample)
* Minfi imports raw data from a folder containing a series of IDAT files and a SampleSheet, which is the output of the Illumina reader
	* `targets <- read.metharray.sheet(base_dir)` extracts the SampleSheet object from `base_dir`, where there are the IDAT files and the SampleSheet
* Raw data from the experiment are extracted in an RGChannelSet object by using the SampleSheet object
	* `RGset <- read.metharray.exp(targets = targets)`
	* This object contains the raw Red and Green intensities for each probe
	* It is organised at the probe, not target level
	* `Red <- getRed(RGset)` and `Green <- getGreen(RGset)` are helper functions that extract a matrix of channel intesities per probe per sample in the SampleSheet
	* There are various functions that extrac and summarise information from the RGSet
* The `MSet.raw <- preprocessRaw(RGset)` function converts the RGSet in a MethilSet object
	* It is organised at the target level
	* For each locus the methilated and unmethilated signal is reported, idependently of the original channel
	* The helper functions `Meth <- GetMeth(MSet.raw)` and `Unmeth <- GetUnmeth(MSet.raw)` return the respective matrices organised per IlmnID (target locus)
* The `GenMetSet <- GenomicMethilSet(MSet.raw)` function converts the MethilSet into a GenMetSet object
	* It is like the MetSet.raw, but mapped to a genome
* The `RatioSet <- RatioSet(MSet.raw)` function converts the MethilSet into a RatioSet object
	* It includes for each target the $\beta$ or $M$ value and, optionally, the copy number
* Applying either `RatioSet(GenMetSet)` or `GenomicMethilSet(RatioSet)` converts the data to a GenomicRatioSet object
	* It is like the RatioSet object but mapped to a genome
* For each Type I probe not only the relevant channel is stored, the instrument measures both Red and Green everywhere
	* The opposite channel is useful for estimating background and it is called out of band probe
* I can create a QC plot for checking the quality of the experiment
	* `qc <- getQC(MSet.raw)` generates a dataframe with a row per sample
		* For each sample the median methilated and unmethilated signal is reported
	* `plotQC(qc)` plots the medians in a log plot
		* Bad samples with low medians are highlighted
* Control probes are present in the array and they can be queried
	* Sample independent controls allow to determine the quality of the processing steps
		* These are staining, extension, target removal and hybridization controls
	* Sample dependent controls allow to determine the quality across different samples
	* These are bisulphite conversion I and II, Specificity I and II, nonpolimorphic and negative controls
* Negative control probes are random permutations of existing probes that should not bind in the genome
	* Their signal should be in the 100-1000 range
	* If they show high signal this could indicate poor sample quality
* Staining control probes have bioitin/DNP already attached and measure the efficiency and sensitivity of the staining step
	* They should give red/green signal according to the marjer they have (biotin/DNP)
* Extension control probes have a final hairpin and therefore they are extended without any target
* Hybridization controls measure the efficiency of binding to sybthetic targets
	* The targets are available in medium, high and low concentrations
	* They should give only green signal
* Target removal controls are not-extendible probes which hybridise with a synthetic target
	* The target is extensible, but if it is correctly removed it should not give any signal
	* The target gives green signal, and there should be no signal
* Bisulphite conversion controls query a non-CpG C/T polimorphism created by the conversion
	* There are both of type I and type II
	* They should give UnMeth signal in type I and Red in type II
* Specificity controls check non-specific extension by querying non-polimorphic sites (always a T)
	* There are both of type I and type II
	* They always should give only Red signal in type II, and non methilated signal in type I
* Non-polimorphic controls also query a non-polimorphic site (but A, T, C, or G)
	* They check the performance of amplification
	* They are of a single type
	* They should give signal according to the queried position
* The p-value of a probe is measured from the background model
	* Low-scoring probes should be filtered out
* A SNP on the target site of a probe or on the flanking base (for type I) alters the results!
* A SNP near the 3' of a probe can alter the result, depending on how close it is to the 3'
