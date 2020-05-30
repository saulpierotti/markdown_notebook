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
* Population standard deviation: $$\sigma = \sqrt{\frac{1}{N}\sum_{i=1}^N (x_i - \mu)^2}$$
* Unbiased Sample standard deviation: $$S = \sqrt{\frac{1}{N-1}\sum_{i=1}^N (x_i - \mu)^2}$$
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
$$MAD = Median(|x_i - \tilde{x}|), \qquad \tilde{x} = Median(x)$$
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
	* In the log-normal model for the natural logarithm when I am using the standard deviation of the logged intensities
$$CV = \sqrt{\exp{\sigma^2}-1}$$
	* If I am using logarithms in base 2 I need to correct the standard deviation by $\ln{2}$
$$CV = \sqrt{\exp{(\sigma*\ln{2})^2}-1}$$
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
$$\log_2{PM_{ij}} = \alpha_i + \beta_j + \epsilon_{ij}$$
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

## Illumina Beadchip
* Illumina BeadChip is a technology for producing high density microarrays
	* These are denser than photolithography
* The array contains 3 um pits where silica beads can be held by VdW and electrostatic interactions
* Each bead is coated with millions of copies of the same oligo
* The beads are assembled randomly on the chip, so a priori their adress is unknown
	* Typically more than 1 bead (14-30) with the same oligo are added to each array
* The oligos of the beads contain a 29 nt barcode and a 50 nt target-specific portion
	* The barcode is used for bead identification
* Illumina produces standard BeadChips arrays for various applications, and also custom arrays
* It is possible to order custom arrays in the format of a microscope slide (Sentrix BeadChip)
* It is also possible to order custom arrays in the format of grids of arrays arranged like a 96-wells plate (Sentrix Martrix Array)
	* In this case each sub-array is etched in the surface of glass fibers for easier reading

### Infimium methylation arrays
* Illumina Infimium chips are standard BeadChips used for methylation studies
* In humans 70% of CpG dinucleotides are methilated as 5mCpG
* Short regions of high CpG density, CpG islands, are unusually unmethylated
	* They are found on 60% of gene promoters
	* Cancer cells tend to be globally hypomethylated but with tumor suppressor promoters hypermethylated
* In a single cell for a single position methylation can either be 0%, 50% or 100% in a diploid
	* When I evaluate methilation with an array I do NOT work on single cells!
	* Methilation can take any value between 0% and 100%
	* Nonetheless, usually I observe a bimodal distribution clustered around 0% and 100%
* DNA methilation islands have a terminology such as shelf, shore, open sea, north and south (upstrean and downstream) in relation with a real island
	* The methilation level of shores seems more correlated with gene expression than the island itself
	* In general, one element of a CpG region (i.e. its shore) is considered a functional unit and it is expected to be coherently methylated
* HumanMethylation27 BeadChip was the first Infinium array 
	* It had 27K probes, more or less one in each CpG island
	* It had only Infinium I chemistry
* HumanMethylation450 BeadChip has 450K probes
	* For each island I have a bead for the island, for the shore, the shelf, the open sea
	* It has both Infinium I and Infinium II probes
	* Infinium I is mostly used in CpG islands (CGIs), while Infinium II in intergenic regions
	* In a single chip 12 samples can be run in parallel
* The last chip, the HumanMethylationEPIC, has 850k probes
	* It contains also probes outside CpG islands, non-CpG methylated sites in stem cells (CHH sites), differentially methylated sites in tumors, FANTOM5 (functional annotation of mammals project) enhancers, ENCODE enhancers and open chromatine, DNAse hypersensitive sites, miRNA promoters
	* It retains 90% of the probes in the Human Methylation 450k beadchip
	* It has Infinium I and II chemistry
* Bisulphite conversion: I can deaminate only non-metilated cytosines to uracil
	* The methyl group protects cytosine from deamination
	* PCR does not reatin methylation patterns so I cannot amplify my sample!
* Genotyping or sequencing the DNA before and after bisulphite treatment I can see which sites are methylated by comparing the C/T differences
* Infinium probes have as a last nucletide the one that pairs with the methylated site (Infinium I) or just before it (Infinium II)
	* An Infinuim array contains both probe types, aiming at different loci
* A single-base reaction extends the probe using the target sequence
* Labelled nucleotides are used, so that the occurrence of extension can be seen by fluorescence
	* A and T are labeled with DNP
		* A/T is colored red with anti-DNP-red
	* C and G are labeled with biotin
		* C/G is colored green with straptavidin-green
* Infinium I assay: 1 color
	* It uses a bead for unmethylated C (U probe) and one for methylated C (M probe)
	* The U probe ends with A (and thus binds T) at the target site, the M probe ends in G
	* U probes can extend only unmethylated sites and vice versa
	* The color of the signal is not improtant here, just its intensity
		* Depending on the base following the CpG, there are RED and GREEN probes emitting on the respective channels
	* Since the probe is 50 nt, it can span multiple CpG sites
		* The methilated probe is built with the assumption that all the included sites are methilated (C/G in C of CpG)
		* The unmethilated probe is built with the assumption that all the included sites are not methilated (A/T in the C of CpG)
		* This assumption is reasonable in islands but not so much in the open sea
* Infinium II assay: 2 colors
	* It uses just one bead per site, with the last position just before the target site
	* Nucleotides are differently marked for methylated (C, G) and unmethylated (A, T)
		* Methilated sites are GREEN, unmethilated sites are RED
	* The methylation is evaluated in the same way as with Infinum I, but with the instensities coming from different channels of the same bead
	* It does not make any assumption about the state of other CpGs included in the probe
		* It uses degenerate R sites that bind both G and A
		* The all or none approach is not possible since the same probe must bind both methylated and unmethilated sites!
	* Since it uses just 1 bead per site with Infinium II I can include a double number of sites in the array
* The raw R/G channel intensities are converted to $\beta$ values
* The $\beta$ value is evaluated as the the ratio among methilated intensity and methylated and unmethylated intensity
$$\beta = \frac{m}{m+u+100}$$
	* $\beta$ values can go from 0 to ~1
	* 100 is added at the denominator to avoid division by 0
* Infinium II is less sensitive to extreme methilation values and less precise
	* Infinium II $\beta$ values have a smaller range than in Infinium I
	* Infinium II $\beta$ values are more shifted toward the center (the distribution is less bimodal)
	* Infinium II $\beta$ values have higher variance between replicates
* When possible, it is better to use Infinium I probes!
* $\beta$ values have an heteroscedastic distribution
	* Its variability (error!) is unequal across its range
	* Middle values tend to be more variable than values close to 0 or 1
	* Many regression models assume a constant error rate across the range (homoscedasticity) so this is a problem!
* The M value is the logarithm of the ratio of methilated and unmethilated signal
$$M = \log_2{\frac{m}{u}}$$
	* It is homoscedastic since the central, more variable region is condensed and the less variable extreme regions are streched
	* It can take any real value, and when $m=u \implies M=0$
	* If $m=0$ or $u=0$ $M$ is considered $-\infty$ or $+\infty$
* Comparing Infinium I and II experiments can be done with intra-array nomalisation (peak-based correction, PBC)
	* This is an approximation method, but it reduces the variance of Infinium II data and it makes the Infinium I and II peaks superimposable
	* Peaks for the Infinium I and II M values are determined using kernel density estimation
	* I rescale the M-values using the respective peak summits as references
	* Rescaled Infinium II M values are rescaled again to match the Infinium I range and converted back to $\beta$ values
	* This makes Infinum I and II data ($\beta$ values) comparable and reduces the variance of Infinium II data
	* PBC depends on the bimodal distribution of the results and breaks down when this is not well-defined!
* I can also normalize Infinium data for addressing dye bias and other sources of technical variability
* Between array normalization can be done using quantile normalization
* If the variance observed is not due to technical errors but to true biological variability, do not normalize!
* Normalization in general assumes that most of the observed variability is error
* It is ok to normalize when I am interested in subtle biological differences
* Cytosine methylation can also be studied by bisulphite-WGS (WGBS) or methylated DNA immunoprecipitation (MeDIP)
	* MeDIP uses 5mC-specific antibodies
* The prof published a paper about the use of the methylation levels of the gene ELOVL2 as an ageing marker
* Peripheral blood mononuclear cells (PBMCs) are a vast range of immune cells
	* They include mainly linfocytes and monocites
* In another paper the prof observed that semi-supercentenarians and their offspring have a decreased PBMC epigenetic age
* It is notable that Infinium arrays are not able to distinguish methylation (5mC) from hydroxymethylation (5hmC)
	* It would be useful to develop a new assay able to distinguish them

# Analysis of differentially expressed genes
* Data analysis is the most important part in microarrays bioinformatics
* The questions that we want to answer generally are
	* Which genes are differentially expressed among samples?
	* What are the relationships between the genes or samples being measured?
	* Can we classify samples based on gene expression?
* In general all the statistical test that we will see in this section look in parallel at one gene at a time and draw conclusions for each gene
* Data can be paired or unpaired
	* In unpaired data different samples have no relationship to each other
	* In paired data I typically have the same sample twice before and after a certain treatment, or in different conditions
	* In paired data I am interested in the expression changes among samples in a pair, while in unpaired data I am interested in changes in the expression of the whole groups
* I can also have complex data, with many groups of different cardinality
* In statistical inference I infere parameters of the population from sample parameters
	* It is important that my sample captures the full variability of the population, so I may want to include different age groups, conditions, ecc.
	* We do not know the level of population variability from which we draw samples
* The fold change ($FC$) is calculated as 2 to the power of the log_2 ratio ($L2R$) of expression
$$ FC = x_1/x_2 = 2^{L2R}, \quad L2R = \log_2{FC}$$
* In order to claim differential expression, in the old days of microarray experiment would choose a fixed threshold of log expression change
	* This does not take into account the variability of the measurement and the sample size
* Hypothesis testing is a more robust way to determine the significance of a variation in expression
	* It assumes the null hypothesis $H_0$ that there is no real biological variation among the samples
	* I can calculate the probability of observing a measurement at least as extreme as the one observed when assuming $H_0$
		* This probability is the p-value
	* Differentially expressed genes are then selected on the basis of a p-value threshold, not according to fold change
	* Note: all the probability statements are referred to $H_0$!
		* Evidnece against $H_0$ is not evidence in favor of any particular $H_A$
		* Bayes!
	* $\alpha$ is the probability of rejecting $H_0$ when it is true (type I error)
	* $\beta$ is the probability of not rejecting a false $H_0$ (type II error)
	* A stringent significance threshold (p-value) increases $\alpha$ and decreases $\beta$
	* Actually, the p-value threshold is by definition my $\alpha$!
	* The power of a test is defined as the probability of observing a real positive
		* It is $1 - \beta$!

\begin{align*}
p \leq \alpha \implies \mbox{ reject } H_0 \\
p > \alpha \implies \mbox{ not reject } H_0
\end{align*}

* Claiming differential expression of a gene means that the expression level of a gene changes systematically between different samples
	* The magnitude of the difference is not relevant
* Two measurements are independent if knowing the value of one measurement does
not give information about the value of the other
	* Measurements of the same gene in different patients are independent
	* Replicate measurements of the same gene in the same patient in the same condition are not independent
* All the statistical tests here described require independence of measurements
	* If I have dependent measurements I need to combine them in a single variable
* Note: in these tests I am not using data from the whole array, but only 1 gene across all the samples!

## Shapiro-Wilk normality test
* The Shapiro-Wilk test returns the p-value for the null hypothesis that the data are drawn from a normally distributed population
* It should not be significant in order to apply parametric tests!
* It calculates the $W$ statistics, that does not have a defined analytical distribution
	* The cutoff values are obtained by MonteCarlo simulations
* $W$ is the ratio between 2 values
	* The numerator is the square of the sum of the products of
		* $a_i$, a coefficient made of strange vector operations
		* $x_i$, the datapoint of rank $i$
	* The denominator is the sum of squared distances from the mean of all the datapoints
$$ W = \frac{(\sum_{i=1}^n a_i*x_(i))^2}{\sum_{i=1}^n (x_i - \bar{x})^2} $$

## Parametric statistics
* Parametric staistics assumes that the population follows a type of probabilioty distribution
	* That is, it infers parameters of the putative distribution
	* It also assume homoscedasticity (uniform variance)
* It is usually more powerfull than non-parametric statistics but it makes more assumptions

### Paired *t*-test
* The paired *t*-test is also referred to as one-sample *t*-test
* It is used for paired data since those are not independent and need to be combined in a single variable
	* Instead of using each measurement as a datapoint, for each patient I have just 1 datapoint which is the difference among the measurement before and after treatment
*  Central idea
	* I assume that there is no difference among pairs of data, so the average of the datapoints is assumed to be 0
		* Datapoints are the differences of paired measurements!
	* If I assume the true average to be 0 but I observe an actual average which is $\bar{x} \not= 0$, I want to know how likely it is to observe that average under the assumption
	* The $t$ statistics that I evaluate is $\bar{x}$ itself corrected for sample size and variance
		* If the sample size $n$ is bigger the result is more significant
		* If the variance $s^2$ is smaller the result is more significant
* From this single column of data I calculate the $t$ statistics
$$t = \frac{\bar{x}}{s/\sqrt{n}}$$
	* $n$ is the number of samples
	* $\bar{x}$ is the sample mean
	* $s$ is the sample standard deviation
* The $t$ statistics is then used to calculate a p-value using the *t*-distribution with appropriates degrees of freedom
* The degree of freedom is the muber of independent variables in the analysis
$$df = n - 1$$
	* in the paired *t*-test it is the number of patients - 1
* When $df \to \infty$ the t distribution approximates a normal distribution
* For lower df the t distribution has heavuer tails than the normal distribution
* The *t*-test is available in all the major software packages and libraries
* This test requires that the differences among the paired samples (the distribution tested!) be normally distributed

### Unpaired *t*-test
* The unpaired *t*-test is also called two-sample *t*-test
* It is really similar to the paried *t*-test, only changing the exprimental design
* In this case my $H_0$ is that the mean of the 2 patient groups is equal
$$H_0:~ \bar{x_1}-\bar{x_2} = 0$$
* Central idea
	* The same concept as for the paired *t*-test, but in this case I explicitly assume the difference of the sample means to be 0
		* I do not have a condensed variable as before!
	* The difference of means is corrected for squared root of the weighted average of the variances of the samples, weighted on sample size
* There are actually two variations of the unpaired *t*-test
	* Welch's *t*-test allows for different variances for the groups and it is better for microarray data
	* Student *t*-test assumes uniform variance and it is best suited for groups of the same size
* This test requires that both datasets be normally distributed
* The $t$ statistics is calculated with a formula similar to the paired *t*-test
	* The formula is different for Welch's and Student's tests
	* Also the degrees of freedom ar calculated differently

#### Student's unpaired *t*-test
* This variant calculates a single variance $s^2$, which is essentially the standard error of the 2 sample means
\begin{align*}
t = \frac{\bar{x_1}-\bar{x_2}}{\sqrt{s^2(\frac{1}{n_1} + \frac{1}{n_2})}}\\[2em]
s^2 = \frac{\sum_{j=1}^{n_1}(x_j-\bar{x_1})^2 + \sum_{i=1}^{n_2}(x_i-\bar{x_2})^2}{n_1+n_2 - 2}\\[2em]
df = 2n-2
\end{align*}

#### Welch's unpaired *t*-test
* In this case I am using the real variances of the samples $s_1$ and $s_2$

$$
t = \frac{\bar{x_1}-\bar{x_2}}{\sqrt{\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2}}}
$$

* The degrees of freedom are calculated with the complicated Welch–Satterthwaite approximation

\begin{align*}
df \approx \frac{(\frac{s_1^2}{n_1} + \frac{s_2^2}{n_2})^2}{\frac{s_1^4}{n_1^2*v_1}\frac{s_2^4}{n_2^2*v_2}} && \mbox{ where }&&
v_1 = n_1 - 1 &&
v_2 = n_2 - 1
\end{align*}

## Non-parametric statistics
* These method do not make any assumption about the distribution of data
	* They are preferred in presence of outliers and noisy data
		* Microarray data is noisy!
* Microarray data analysis is high throughput, so it can be unpractical to check for normality
* There are 2 types of non-parametric tests
	* Classical non-parametric tests are equivalent to parametric tests but use ranks instead of actual data
	* Bootstrap tests are more modern and can be applied to a wide range of analyses
* When to use non-parametric statistics
	* Data better represented by the median
	* Small sample size, so the distribution is diffucult to evaluate
	* I have ordinal or ranked data
	* There are outliers that I cannot or don't want to remove

### Classical non-parametric statistics
* These tests are implemented in R, but not in Excel
* They are less powerful than parametric and bootstrap methods
	* Because of this, for microarray data bootstrap methods are preferred

#### Wilcoxon sign-rank test
* The Wilcoxon sing-rank test is the non-parametric equivalent of the paired *t*-test
* The $H_0$ is that the median of the dataset is 0
	* This is a paired test, so the dataset is the difference among pairs of data!
* It replaces the real data with ranks according to the absolute magnitude of their difference (or log ratio for microarrays)
	* I first compute the differrences among pairs of data, and I take the absolute value of this difference
		* If the difference is 0 I exclide the pair of data
	* In the meantime I note down which differences were positive and which negative (the sign!)
	* I perform the ranking on the absolute differences among pairs of data
	* The smallest datapoint has rank 1, the largest has rank $n$, and so on
		* If 2 values are the same I take the ranks available (i.e. 2 and 3) and assign to both datapoints their average (i.e. 2.5)
* I compute the sum of all the positive and negative ranks
	* The sum of positive ranks is called $W_+$, the sum of negative ranks $W_-$
* The $W$ test statistic is the smallest absolute value among $W_+$ and $W_-$
* Intuition: a small $W$ means that the distributio of ranks is heavily skewed towards the positive or negatives
	* If positives and negatives are balanced, $W$ is at its maximum
	* If all the ranks are positive/negative (and so there is a systematic effect) $W=0$ since one of the classes is empty
* The $W$ statistic is compared against the W distribution to obtaine a p-value
	* The $W$ is significant if smaller than a threshold value
* Albeit not requiring normality of the data, it requires them to be symmetric

#### Mann-Whitney U test
* The non-parametric equivalent of the unpaired *t*-test is the Mann-Whitney test, also called Wilcoxon rank-sum test
	* It is similar to the Wilcoxon rank-sign test
* The $H_0$ is that the median of the 2 datasets is equal
* Data from the 2 groups are combined and ranked together
	* Ties are treated in the same way as in the Wilcoxon sign rank test
* I sum separately all the ranks for the 2 groups getting the repsective rank sums ($R$)
* I calculate the $U_A$ and $U_B$ statistics separately for the 2 groups
$$U = R - \frac{n(n+1)}{2}$$
	* $n$ is the number of samples in the respective group
* The final value of the $U$ test statistic is the smaller value among $U_A$ and $U_B$
* I then compare $U$ against a pre-computed $U$ distribution and I reject $H_0$ if $U$ is smaller than a threshold

## Bootstrap analyses
* Bootstrap is based on resampling with or without replacement
	* In general both variants give really similar results, there is debate on which one is better
* Bootstrap analyses are non-parametric tests so they do not make any assumption on the distribution of the data
* They are more powerfull than classical non-parametric tests
* They should be preferred on microarray data than either parametric and classical non-parametric tests
* They are quite computationally expensive
* There are bootstrap equivalents for paired and unpaired tests, and also for ANOVA, cluster analysis and other more complex tests
* I do resampling and evaluate the $t$ statistics in each bootstrap
* I produce a distribution of $t$ after thousand of bootstraps
* It is recommended to do a number of bootstraps which is at least 10 times the number of genes in the array

### Unpaired *t*-test bootstrap
* This is the easiest bootstrap implementation
* The $H_0$ is the usual for the unpaired *t*-test: no difference among the mean of the groups
* If the $H_0$ holds, any of the measurement in the data could have been obtained from any of the individuals
	* I create thousands of random datasets by resampling the original data but redistributing randomly the measurements among indivduals of BOTH groups
	* If I use replacent the same datapoint can be assigned to 2 different individuals
* I calculate the $t$ statistic from each of the randomized datasets, without correlating it to a p-value
* I then compare the $t$ from the real data with the bootstrap $t$s
* I determine the p-value according to the proportion of bootstrap $t$s that are more extreme than the actual dataset $t$
$$ p = \frac{count(|t_{bootstrap}| > |t_{real}|)}{n_{bootstraps}}$$
* I the real $t$ is on the edges of the empirical $t$ distribution, then it is probably not due by chance
* Basically I evaluate the p-value from the empirical $t$ distribution instead than on the theoretical ones (which are calculated on normally distributed data!

## Multiple testing
* If I am testing multiple times the same dataset I risk to get an unacceptably high number of false positives
* The false discovery rate (FDR) is the percentage of rejected $H_0$ that were true
$$ FDR = \frac{FP}{FP+TP}$$
* I can decrease the p-value threshold, but this is a tradeoff: I will decrease the false posiitve rate but increase the false negative rate
* The only way to decrease the false positive rate and also the false negative rate is to increase the sample size

### Bonferroni correction
* The Bonferroni correction for multiple testing is simple: just divide the desired p-value threshold on a single test by the number of tests
	* An equivalent approach is to retain the desired p-value threshold but multiply the obtained p-value by the number of tests
	* It is usually too stringent for microarray analysis, not yelding any significant result

### Benjamini Hochberg q-value correction
* The Benjamini-Hochberg correction for multiple testing is based on the FDR
* I frist rank all the p-values in ascending order
* I calculate from the p-values the respective q-values
$$ q_i = \frac{p_i*N}{i}$$
* The numerator $p_i*N$ is the ith smallest p-value observed times the number of tests done (and so the number of p-values)
	* It is essentially the expected number of unjustified rejections of $H_0$
	* It is the number of false positives
* The denominator is the actual number of results accepted for that p-value
* If the denominator is bigger than the numerator, I have more significant results than expected by chance, so some of them are probably actually true

## ANOVA
* With microarray data I can want to compare more than 2 groups, or more than 1 variable
* The analysis of variance (ANOVA) test is a generalization of the t test for more than 2 groups
* The one-way ANOVA is used for comparing ONE variable across more than 2 groups
* The two-ways ANOVA is used for comparing 2 variables across more than 2 groups
* ANOVA is parametric and it assumes normal distribution with equal variance
* I can do bootstrap when these assumptions are not true

## One-way ANOVA
* It returns a single p-value for the null hypothesis that there is no difference among the means of all the groups
	* It does not tell me which group is different if the result is significant!
* It is based on the $F$ statistic, compared against the F-distribution
* I assume that all the variance inside a group is due to error, and all the variance between group which does not depend on the internal variance of the groups is real biological variability
$$ F = \frac{SS_b}{SS_w} = \frac{\sum_{j=1}^{m}n_j(\bar{x}_j-\bar{x})^2}{\sum_{j=1}^m \sum_{i=1}^{n_j} (x_{ij}-\bar{x}_j)^2}$$
* $SS_b$ is the sum of squares in between the groups and $SS_w$ is the sum of squares within the groups
* $i$ is the index of samples in a group, $j$ the index of groups
* $n_j$ is the number of samples in group $j$
* $m$ is the number of groups
* $\bar{x_j}$ is the mean of group $j$, $\bar{x}$ is the grand mean of the whole dataset
* $F$ is large (more significant) if the variance within the groups is small while the variance among groups is large
* Under $H_0$ $F$ has a mean of about 1
* If I have only 2 groups the one-way ANOVA reduces to the *t*-test with $F=t^2$
* The $F$ distribution has 2 parameters, the degrees of freedom for numerator and denominator
	* The degrees of freedom of the numerator ($SS_b$) is $m-1$, with $m$ being the number of groups
		* I have $m$ groups, and from them I estimate the grand mean
	* The degrees of freedom of the denominator ($SS_w$) is $n-m$, with $n$ being the number of total samples and $m$ the number of groups
		* I loose one degree of freedom for each group since I estimate the mean
		* I have $n$ samples amnd estimate $m$ means (1 per group), so I have $n-m$ degrees of freedom

## Kruskal-Wallis H test
* It is a non-parametric test that estends the Mann-Whitney U test
* It is the non-parametric version of the one-way ANOVA, operating on ranks instead of actual data
* The null hypothesis is that no group stochastically dominates on the others
	* If I can assume the same distribution (non necessarily normal) for all groups, then the null hypothesis is a statement about the equivalence of group medians
* The data from all groups are ranked like in the Mann-Whitney U test
* The test statistic $H$ is calculated as
$$ H = (N - 1) \frac{\sum_{j=1}^m n_j (\bar{r}_j - \bar{r})^2}{\sum_{j=1}^m \sum_{i=1}^{n_j} (r_{ij} - \bar{r})^2} $$
* $n_j$ is the number of observations in group $j$
* $r_{ij}$ is the general rank (across the entire dataset) of obervation $i$ from group $j$
* $N$ is the total number of observations
* $\bar{r}_j$ is the avergae rank of all the observations in group $j$
* $\bar{r}$ is the average of all the ranks
* There is also a simplified formula for when there are no ties
$$ H = \left(\frac{12}{n(n+1)}\sum_{j=1}^m \frac{T_j^2}{n_j}\right) -3(n+1)$$
* If using the simplified formula in presence of ties an adjustment is needed, according to the number of ties $t$

\begin{align*}
H_{adj} = \frac{H}{D}, && \mbox{where} \quad D = 1 - \frac{\sum (t^3 - t)}{(n-1)n(n+1)}
\end{align*}

* The $H$ statistics has an approximate $\chi^2$ distribution with $m-1$ degrees of freedom
	* Calculating the exact distribution of $H$ is computationally complex
		* Tables are available up to 105 samples
	* If possible is better to use computed $H$ thresholds instead of the $\chi^2$ distribution
		* The 2 distributions diverge sensibly when there are small groups
* I reject the null hypothesis if $H > \chi^2_\alpha$

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
