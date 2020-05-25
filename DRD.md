% DNA and RNA dynamics
% Saul Pierotti
% \today

# Introduction
* Professor works in human aging
* Module 1 has a written test, module 2 a report (of course)
* Final score is 20 (module 1) + 10 (module 2)
* Experimental questions should be focused
* In an experiment I have to consider experimental and biological variability
* We can find nucleosomes in blood deriving from apoptotic bodies
	* They are found in microvescicoles
	* Sometimes they can also be free and in this case they are dangerous
* In the lab of prof. Capri they tryed to see if the nucleosome-associated DNA in blood is different in young, old people and centenarians
	* They work a lot with centenarians and they are so proud of it
* We have about 28 millions CpGs in our genome
* Histones are octamers
	* H2a and H2b form a dimer
	* 2 H3 and H4 form a tetramer
	* A tetramer binds 2 dimers forming the histone octamer
	* Toghether with 148 bp of DNA they form nucleosomes
	* The DNA between nucleosome is called linker DNA
	* H1 is the linker histone which binds incoming and outgoing DNA from the nucleosome
* Histone modifications are one of the essential epigenetic modifications
	* Histone modifications: metilation, acetilation, posphorylation, ubiquitinilation
	* They usually happen in K, R, S, or T of histone tails
	* Histone variants (es. H2ax) mediate also functional alterations
	* H3k4me3 is typical of active promoters
* TET (Ten Eleven Translocation) is the principal CpG demetylating enzyme
* DNMT1, DNMT3a and DNMT3b are the principal methylating enzymes
	* DNMT1 mainly methylates hemimethylated CpGs
	* DNMT3 performs mainly de novo methylation
* In mammals metilation happens mostly at position 5 of C in a CpG dinucleotide
* High expression is associated with high gene metilation and low promoter metilation
	* The causality is not so clear
* The inheritance of mathylation patterns is not clear
* CpG methylation can be used as a marker of ageing and pathology
* The metaorganism: nDNA, mtDNA, microbiome
	* Microbiome influences our phenotype
* The Human Microbiome Project (HMP) aimed at sequencinge the microbiome genome
	* The microbiome genome was shown to have more than 33 million genes
* RNA expression changes in response to stimuli
* RNA are of many types
	* lncRNAs are longer than 200 nt
	* sncRNAs are shorter than 35 nt
	* Middle-sized RNAs
		* Structural: tRNA, rRNA, snRNA, snoRNA
		* Regulatory: ncRNA, siRNA, miRNA, piRNA
		* tRNA derived fragments (tRF) are involved in several functions like stress response
* Micro RNAs: pair with mRNA in an inextact way and block translation
	* miRNAs are 18-25 nt long
	* They can have many targets, that they recognize through pairing of their seed sequence
	* They regulate 60% of the mRNAs
	* Humans probably have around 600 miRNAs
	* Each locus can produce 2 miRNAs (5p and 3p), complementary to each other
	* They are in intergenic regions or in introns or also exons!
	* pri-miRNAs are transcribed by RNA-Pol-II under the control of specific promoters
		* They form a carachteristic hairpin structure
	* pri-miRNAs are cut by the microprocessor (Drosha(Pasha)/DGCR8) to pre-miRNA
		* Drosha is a type III class II RNAse
	* pre-miRNA are exported from the nucleus by the Ran-GTPase Exportin 5
	* Dicer/TRBP trims the pre-miRNA in the cytosol to a miRNA duplex and separates the 5p and 3p miRNAs
	* The miRNA takes part in the RISC complex and it silences mRNAs
	* miRNAs can be found in vescicles/exosomes and go around the body
		* They can act in different cells than the ones that produced them!
* Astronauts could be ageing faster
	* They want to check their DNA associated with nucleosomes before going, after landing and after a while after landing
* I can distinguish biological and experimental variability by carefully designing my experiment
	* Biological variability is usually a lot
	* I should always do technical replicates
* When planning an experiment it is essential to know the underlying biology in order to select the correct variables

# Basic statistics
* $\mu$ and $\sigma$ refer to population parameters, while $\bar{X}$ and $S$ are sample parameters
* Coefficient of variability: $CV = (SD/\bar{X})*100$
* Population standard deviation: $\sigma = \sqrt{\frac{1}{N}\sum_{i=1}^N (x_i - \mu)^2}$
* Unbiased Sample standard deviation: $S = \sqrt{\frac{1}{N-1}\sum_{i=1}^N (x_i - \mu)^2}$
	* The standard deviation estimated from a sample must divide by the degrees of freedom!
	* I already estimate the mean using the data so I loose 1 df
	* The mean of the sample is likely to be closer to the values in the sample than to the general population since it was estimated from them!
	* I consistently underestimate the variance if I divide by N!
* The standard normal distribution has mean $\mu = 0$ and standard deviation and variance  $\sigma = \sigma^2 = 1$
	* $\mu \pm 1 \sigma$ are the inflection points of the curve and include 68.2% of the population
	* $\mu \pm 2 \sigma$ includes 95.4% of the population
	* $\mu \pm 3 \sigma$ includes 99.6% of the population
	* The Z score is the number of $\sigma$ away from the mean in the standard normal curve that my measurement is
* Box plot: look at data distribution
	* The central line is the median (quartile Q2)
	* The sides of the box are the quartiles Q1 and Q3
	* The interquartile range (IQR) is Q3-Q1 and contains 50% of the distribution
	* The wiskers are 1.5*IQR above/below Q1/Q3
	* Outliers are the datapoints outside of the wiskers

# Microarrays
* Tiling arrays cover an entire genome
	* They can be designed so to study gene variants, transcripts, DNA methylation, chromatine immunoprecipitation, ecc...
* There are DNA and protein arrays (Ab arrays!)
* For transcriptomics and DNA metilation I can use competitive or non competitive arrays
* Production technologies
	* Oligos can be separately synthesised and spotted (various companies do this)
	* DNA can be synthesized directly on the chip (GeneChip)
	* Oligos can be separately synthesized and loaded on beads, which are then immobilised on the chip (BeadChips)
* Microarray supports can be made of glass, silicon, quartz, nylon
* Competitive microarrays use 2 color channels in order to quantify the relative abundance of 2 different species
* Non-competitive microarrays use just 1 color channel to give an absolute estimate of a species
* Spotting technique: the oldest approach
	* A spotting robot with pins spots oligos in the slide
	* The glass chip surface can be coated with aminosilane or other amino-modified groups for binding oligos
		* This is feasible with longer oligos, that are long enogh to interact strongly with the support
	* I can use oligos with a 5' alifatic amine that binds to the glass
		* This is typically used for shorter oligos
* In situ synthesis of oligos
	* I synthesize oligos on the slide itself base by base
	* I use dNTPs with a protective group at the 5' that inhibits elongation
	* I selectively deprotect the 5' in different ways
* I can use UV exposure to deprotect the 5', so that sinthesis can continue (Affimetrix)
	* I can determine the sequence of each probe by using photolitographic masks to selectively expose probes to UV light
	* UV masks are expensive to produce, but once produced they can be used for many arrays
	* This technique is highly scalable and it is suityed for standardized (non-custom) arrays
* Affimetrix mask deprotection generates rectangular features
	* There is refraction of UV light in the mask, so there is bleeding among adjacent features
	* The Affimetrix software corrects this by using only the central pixels of each feature
* Other approaches are more suited for custom arrays
	* I can unse maskless photodeprotection with micromirrors
	* I can use inkject chemical deprotection
		* This gives the highest-quality features

## Competitive microarrays
* They use 2 colors in the same chip and they were invented 20 years ago at Stanford by Patrick O'Reilly Brown
* Tipycally they are used with mRNAs: I do retrotranscription using Cy3(green)/Cy5(red) marked nucleotides for different samples
	* Ibridization is usually overnight, then I scan the array and acquire the image
	* I can then compare expression level by comparing Cy3/Cy5 intensity at each spot
* Cy3 and 5 are both N-hydroxy-succimidyl esters but Cy5 is bigger
	* Possible bias during retrotrascription!
	* To reverse this, I can retrotrascribe both samples with aminoallyl-dUTP and then couple the dyes via chemical reaction
* The array scanner (ScanArray) scans at 550nm (green) for exciting Cy3 and at 649nm (red) for Cy5
	* A feature is usually represented by ~50 pixels
	* The laser is separately focused in each pixel
		* This is done by optics or by moving the slide
	* Fluorescence is measured by a photomultiplier tube (PMT) for each pixel
	* I do not read the whole array toghether, I read 1 pixel at a time!
	* Each laser spot size is represented by 1 pixel, or by more than 1
		* If a the pixel size is smaller than the laser spot, I blur the image and reduce irregularities
	* Each pixel of the image is a point of measure
	* The 2 channels are then merged in silico
* For each channel a 16-bit monochromatic TIFF image is acquired
	* A single image can be 32 Mb, so if I scan many arrays storage is an issue
* Each channel TIFF image is processed so to obtain a table of intensities for each feature
	* I first need to find the features
	* Then, for each feature I need to segment it: determine which pixels belong to the feature and wich to the background
* For each spot in the final image, the software uses false colors
	* A white spot is saturated
	* A blue spot is absence of signal
	* A red spot has Cy5 upregulation
	* A green spot has Cy3 upregulation
	* A yellow spot has the same levels of Cy3 and Cy5 intesities
* I can address any possible dye bias by swapping the dyes and repeating the experiment
* Background fluorescence can be a problem
	* The usual approach is to subract the local background from the feature intensity
		* If the result is negative (backgroud is broghter than the feature) I flag the feature as unreliable and filter it out
	* I can assign the arbitrary value 1 to all the features with intensity lower than the background
	* I can use a Bayesian approach to estimate the true feature intensity
* For each spot I have a pixel distribution
	* I can get the mean signal, SD, median, median absolute deviation (MAD)
	* $MAD = Median(|x_i - \tilde{x}|)$, where $\tilde{x} = Median(x)$
	* The MAD is the median of the absolute deviations from the median of the dataset!
* Image scanning is crucial for data quality
	* Low laser intensity for redcing photobleach
	* The photomultiplier shuold be set so to balance the Cy3 abd Cy5 channels
* Segmentation is the process of identifying clusters in the image
	* It is done with algoriths and manual inspection
	* There is also an experimental approach that uses DAPI to color the clusters
* Spot intensities for Cy3 and Cy5 can be use for estimating the overall expression ratio
* The row data intensity is typically transformed in log_2 scale
	* In this way a signal of 1 means a 2-fold upregulation
	* Raw data tend to be highly skewed towards 0, while log data are more normally distributed
		* This is beacuse raw data has a lognormal distribution ($Y\sim\log{N}$)
* The MA plot is useful for evaluating the distribution of data in a competitive array
	* The x (called A) is the log average intensity $(\log{Cy3}+\log{Cy5})/2$
	* The y (called M) is $\log{Cy3}/\log{Cy5}$ ratio
	* It allows to see if the fold change is due to variations in absolute intensity
* If the MA plot is not horizontal I need to normalise my data
	* Linear normalisation: I can assume that the fluorescence of one of the dyes is related to that of the other by a correction factor k
	* This corrects for different absolute intensities of the dyes
	* I just scale M (the y) by subtracting the log2 of the constant k
	* I can center the M to 0 by using c=log2k=median(M)
* Intra-array normalization: use the same reference sample!
	* Variability can derive not only from differential expression
		* Different response of the Cy dyes and of the apparatus at different wavelenghts
		* Different response in different parts of the array (spatial variability)
* All the following methods for intra-array normalization rely on the assumption that the majority of features are NOT differentially expressed
	* Because of the assumption, most of the gross variability is techinical
	* Cy5 to Cy3 linear regression
		* If the 2 dyes are behaving equally, I expect to observe an equally spaced straight line with $m=1$ and $q=0$ when plotting in log space
		* A non-0 intercept means that one channel is systematically brighter
		* A non-1 coefficient means that one channel is more responsive to high intensities
			* Usually Cy3 is stronger at high intensity and Cy5 is stronger at low intensity
		* There can be deviation from linearity
		* I can apply this correction by fitting a linear regression to the data and subtracting the fitted Cy3 values from the raw Cy3 values
		* In this way I am treating Cy3 and CY5 differently so the method is not reversible!
	* MA plot linear regression
		* If the channels are behaving equally I expect an horizontal regression line centerd in $y = 0$
		* This regression treats both channels equally
		* For each datapoint I subtract the fitted log ratio to the raw log ratio
		* This processing makes the linear regression horizontal and centered at $y = 0$
	* In each case when the dependence is not linear I can fit a non-linear model
		* The LOESS regression fits locally a polynomial and then smooths the curve
	* Spatial effects can be due to the array being not horizontal during the scan
		* Some regions can be in focus, others not
* Inter-array normalization: comparing different samples
	* Different arrays can have different data distributions
	* These methods all make the same central assumption: the variations in the distributions between arrays are a result of experimental conditions and do not represent biological variability
	* Data scaling is used to make the means of different distributions equal
		* I just subtract the mean log ratio of the distribution from each datapoint in the distribution
		* An alternative is to use the median instead of the mean
			* The median is less sensitive to outliers and it is more adequate when data is not normally distributed
	* Data centering is used for making the means and standard deviations of the distributions equal
		* It is similar to scaling but in addition I also divide for the standard deviation (or MAD in case of median)
		* All the resulting distributions have a mean of 0 and a standard deviation of 1
	* Data normalisation is used for makeing the distributions identical
		* First I need to center the data and I order, for each array, the centered data from lowest to highest
		* I compute a reference distribution with lowest value the average of the lowest values of each array
			* I repeat this fo the second lowest and so on
		* I replace each measurement with the corresponding average
			* The highest measurement is replaced with the higest value of the reference distribution and so on
		* The resulting distributions are identical and have mean 0 and standard deviation 1
		* I am NOT making all the data equal
			* A certain feature can be first on one array and 15th on another, and so it will have different values
			* The first features of 2 arrays will have the same values, but they can be different features!
* When the assumption of non-differential expression is not reasonable I can use a reference sample for normalization
* In the lognormal model the errors are normally distributed
	* In real data errors tend to have sharper peaks and heavier tails than what the distribution predict
	* The log-normal distribution for microarray data is an approximation!
* Variability in a dataset can be estimated with the coefficient of variation CV
	* In the log-normal model $CV = \sqrt{\exp{\sigma^2}-1}$ for the natural logarithm when I am using the standard deviation of the logged intensities
	* If I am using logarithms in base 2 I need to correct as $CV = \sqrt{\exp{(\sigma*\ln{2})^2}-1}$
* Replicate feature variability is the variability among identical features in different physical positions in the array
* Cy3 to Cy5 variability is best evaluated by self-self hybridization or by swapping dyes
	* Self hybridization means to labele with both dyes the same sample and hybridise it in the same array
* Hybridization variability is the confounded measurement of the variability among hybridization reactions and among arrays
	* I cannot distinguish these 2 variabilities, so they are confounded
	* I can use an identical reference sample in all the arrays to estimate it
	* The distribution of the reference sample is centered in each array
	* I usually filter only features for which data is complete
* Sample (biological) variability tends to be the biggest source of variability, and it is also what we are usually interested in!
* The MIAME standard is used for uniformating microarray experiments and allowing comparisons
	* Many publishers require MIAME compliance!
	* The GEO (Gene Expression Omnibus) database supports MIAME-compliant data!

# Non competitive arrays

## Affimetrix Genechip
* Affimetrix Genechips is a closed platform (only usable with reagents and instruments supplied by them)
* The new form of this kind of chips is called Next generation arrays
* The chemistry was invented in 1991 by Stephen Fodor
* Affimetrix started in California as a startup and then it was acquired by Thermo Fisher
* This arrays are produced by photolotography chemistry
	* It is used for in situ synthesis of oligos!
	* A UV sensitive reaction blocker is selsectively degraded by UV light
	* A UV-sensitive blocker is also used on the glass surface to modulate the addition of the first base
	* It uses also side protections in nucleotides to avoid the formation of branched chains
	* Features are rectangular
* Genechips for the following species are available: *B. subtilis*, barley, cow, *C. elegans*, dog, chicken, *Drosophila*, *E. coli*, human, maize, mouse, *P. aeruginosa*, and many other
* Probes are typically at the 3' of transcripts so that they can recognize also partial mRNAs
* Housekeeping genes have probes both at the 3' and 5' so that I can compare their intensities and estimate sample degradation
* Probes are redundant, in the sense that there are different probes that target different positions of the same mRNA to cross-check and average results
* The set of probes targeting the same genes is called probe set for that gene
* Mismatch probes are probes similar to normal probes but with a single base mutated in the middle
	* They are used to quantify background and non-specific binding and remove it
	* It is also a control for the actual binding: I expect to have a lower intensity that for the real probe but correlated to it
* There are also complete 8-mer and 9-mer chips!
* The human HG-U133 Genechip is a gene array
	* It contains 1.3 million features in a 1 cm*1 cm area
	* It has features for 47400 transcripts on 38000 genes
	* Gene sequences were obtained from public sources
	* It has internal control probes
	* 11 probes at the 3' of each gene to measure the level of transcript
	* More than 54647 probe sets
	* Some genes had more than 1 probe set
* The GeneChip 1 ST array is an exon array
	* It is a perfect match-only design: there are no mismatch probes
	* It has probes on each exon of a gene
	* The background is estimated with 20k background probes that do not bind anything
	* It includes poly-A control probes and hybridization controls

* The Genechip whole-transcript sense target labeling assay can be used for target preparation
	* Targets are sense cDNAs obtained from mRNAs
	* It usually requires 1 ug of RNA
		* The latest kits can work with as little as 100 ng
	* rRNA is first selectively removed
	* First mRNA is reverse-trascribed and then the antisense cDNA made double strand
		* At this step poly-A controls are added
			* They are artificial transcript at precise concentrations with a poly-A to be used for reference
		* I can also amplify the dsDNA at this point
	* The cDNA is in vitro trascribed to cRNA
	* The cRNA is retrotrascribed again to sense cDNA using random primers and dUTP instead of dTTP
	* cRNA is degraded and cDNA fragmented and terminally labeled with biotin
		* The fragmentation happens at dUDPs with UDG and APE1
		* The labeled nucleotide is added with TdT
	* At this step hybridization controls are added
	* After hybridization the array is stained with an avidin-containing dye (streptavidin-phyocoerythrin)
* After staining the array image can be visually inspected
	* The image can be greyscale or in false colors
	* The positive probe sets are in specific locations in the array
		* They can be at the edges are also form words in the array!
	* I can check the shape of features
	* I can check if features are correctly aligned to the grid by the software
	* I can see if there are scratches, dust, washing not complete
* The software used for acquiring and elaborating Genechip data is called AGCC
* The raw image of the array is saved in a .dat file
* For each feature I retain only pixel above the 75 percentile value
	* This usually means that I remove pixels at the border
	* The intensity for a feature is the average of the respective pixel intensities
* The elaborated image has a pixel per feature with intensity that is the average of the pixel above the 75 percentile for that feature
	* This image is saved in a .cel file
* The software does also an automatic data analysis producing a .chp file
	* This is usually discarded and data are analysed manually
* The information about the probes in the array are contained in a .cdf file, that can be obtained from affimetrix
	* A .msk file is also provided that allows to celect certain groups of probes for normalization and scaling purposes
* Affimetrix data can also be analysed with bioconductor packages
	* I can use YAQCStats to get a QC plot, a frequency histogram of the log_2 intensities
* Probes that bind the same transcript can show 2 or more orders of magnitude differences in intensity
	* Probe binding strenght depends on the GC content
	* Match probes can even be weaker than mismatch probes!
	* Variability among arrays for the same probe is orders of magnitude smaller than variations among probes in the same array for probes against the same transcripts!
* Data preprocessing typically involves background correction, normalization and summarization (getting a single value from a probe set across multiple arrays)
* The RMA (robust multichip average) is a normalization procedure based on quantile normalization
	* This is used for treating data from a probe set, not whole arrays!
	* The first step is background correction
	* The log_2 of each perfect match probe intensity is calculated
	* These values are quantile-normalized
	* The normalized values are summarized across arrays and probes
* I fit a multichip linear model to the data
	* $\log_2{PM_{ij}} = \alpha_i + \beta_j + \epsilon_{ij}$
	* $PM_{ij}$ is the intensity of the perfect match probe $i$ in array $j$
	* $\alpha_i$ is the intensity due to the carachteristics of probe $i$ (i.e. GC content)
	* $\beta_j$ is the intensity due to true expression of the trascript in array $j$
	* $\epsilon_{ij}$ is the error in the measurment of probe $i$ in array $j$
* Fitting is done using the Tukey's medianpolish algorithm
	* It produces a two-way layout table where of probes against arrays, filled with the respective intesities
	* It calculates the median of each row (all measurements in one array) and subtracts it from the values
	* It calculates the median of each column (all measurements of the same probe across arrays) and subtracts it from the values
	* It iterates again for rows and columns until all the row and column medians are 0 (or under a threshold)
	* I subtract the obtained values from the original ones to get the fitted values
		* In this way I am scaling all the arrays to the same range with the same distribution!
	* I can then average across probe sets to obtain the RMA average for each chip (row average)
	* This is the final value for the trascript in a given chip
	* If I subtract the row average from the fitted values I get the probe effect values
		* This value is the same for all the chips since they have the same distribution and distances from their respective mean!
* I can do an MA plot also for Affimetrix arrays!
	* I can plot 2 chips agaist each other
* The development of GeneChip array was strongly dirven by the competition with NGS techniques
* The GeneChip Human Trascriptome array 2.0 contains more than 6 millions probes covering coding and non-conding transcripts
	* It is also colled GG-H (Glue Grant human) array
	* It contains also probes for SNPs, alternatively spliced trancripts, ...
* For each GeneChip I can obtain the relative probset ID and annotation on the ThermoFisher website

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
