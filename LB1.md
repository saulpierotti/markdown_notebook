% Laboratory of Bioinformatics 1
% Saul Pierotti
% \today

# 14/11/19
* X-ray diffraction gives us diffracrtion maps
* Diffraction maps are interpreted by Fourier transform to compute the electron density
	* It is a computation-heavy task
* Electron density is used to fit a protein structure
* I compute the diffraction pattern of the theoretical protein structure to check if it matches the experimental pattern within a reasonable tollerance
* The PDB file does not contain the electron density, it is an approximation of the structure
* The only textbook is PDB-101
* The resolution of an X-ray diffraction is imprtant
	* $5.0\AA$ resolution is reasonably accurate only for the position of the backbone
	* $1.5\AA$ can be generally trusted, also for drug design
* We need to know the Bragg diffraction law
* Crio-electron microscopy gives us a diffraction pattern using an electron beam
	* It is really useful for really big complexes that cannot be cristallized
	* Resolution is lower than X-ray diffraction
* A ligand is any molecule co-cristallized with the macromolecule considered
* Biology without structure is fantasy
* Annotation is an inference where you endow with structural and functional features an element
* A PDB file has an unique identifier of 4 letters and numbers
* On PDB I can also find the FASTA of the protein
	* FASTA contains the covalent structure (i.e the sequence) of the protein
	* It is the sequence derived from the structure, it can be different than the one in uniprot (!)
* Signal peptides are 10 to 30 residues in length
	* They are usually cleaved and therefore they do not appear in the protein 3d strucutre
* Coverage refers to the percentage of protein sequences covered in the protein structure
* FASTA has 60 residues per line
* Routinely X-ray diffraction is not able to locate hydrogens
* Each crystal has a unit cell
* PDB files produced using a synchrotron source have 2 spots associated with every atom
* For each ATOM we have the xyz coordinates, the occupancy, and temperature factor
	* Occupancy is how well the atom fits the electron density
	* The temperature factor refers to the mobility of the position
* The PDB file contains the atomic model of a macromolecule
* The CPK colorscheme is a popular set of colors used for the different atoms
* The structure validation window reports the percentile rank of different validation methods
	* Blue is good, red is bad
* DSSP is a program that reads a PDB file and assigns a secondary structure to each PDB coordinate
	* It was made by Sanders, one of the founders of bioinformatics, and Kabsch
