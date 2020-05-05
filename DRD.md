# DNA and RNA dynamics

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
