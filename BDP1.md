# Introduction to Big Data Processing Infrastructures

## Introduction
* This course is not about Big Data, it is about infrastructures
* We should have visited a datacenter, but... Corona
* We need SSH, a little bit of C/C++, vim, Python
* We will use AWS and Google Cloud computing!
* Of course we will make a project and an oral exam
* Prof of course is a physicist of the IIFN
* The IIFN-CNAF hosts the Tier-1 datacenter in Bologna

## Setting up AWS
* It is a pay for use model
* You have at the beginning a 50\$ credit

## Big data
* They tend to be non structured
* They are characterized by 4 Vs: Volume, Variety, Veracity (can I trust them?), Velocity
* Another important point is Value, what I want to extract from the data

## Computational challenge
* Find a substring in a string
* Doing it brute force is really slow
* I can create an index once and then I can search every time much faster
	* It is blast essentially
	* The BWA algorithm is another possibility
		* It is used for more similar sequences
		* It is faster when I have many reads to be aligned
* Using the right approach is much more effective than increasing computational power
* If possible use open source code
	* You avoid vendor lockin and the approach can be scaled more easily
* Creating a new approach from scratch is usually wrong
	* You will not create a good system from scratch
 c* Our challenge: align 554k sequences per patient against the human genome
	* The aim of this course is creating a cloud based model for computing this
	* I also want to estimate the time required

## Some notes
* A checksum is essential when we are moving data
	* It is a small string used to detect error in data transmission or storage
	* It is possible to set an extended file attribute with the checksum (if the file system allows it)
* Files are moved compressed, moving uncompressed files is a crime

## From PC to datacenter
* 1 byte is 8 bits (but we can also use 10 to make it easier)
* A multicore processor has more than 1 processing unit
	* A core appears to the processor as a different CPU
	* A socket is the physical CPU, and it can have many cores
* Hyper-threading is a technology that improves parallelization
	* It operates only at the logical level
	* The OS sees a double number of cores
	* It maximises the exploitation of the processor by running at the same time operations that can be run at the same time
		* An example can be doing an ALU operation and a logical operation at the same time
	* It can improve performances but it depends on the application
	* It can also degrade performance by trashing the cache
* Top shows the status of all the logical cores in the system
	* wa shows the time spent waiting for I/O
	* load average shows the number of processes waiting for enetering in CPU
		* It should be at most equal to the number of cores, otherwise we are in an overloading
* A good source of info for the system is cat /proc/cpuinfo
	* flags shows the capabilities of the processor (instructions)
* Memory is RAM
	* It is volatile and fast
* We typically have a memory hierarchy
	* L1, L2 and L3 cache in the processor
	* Main system memory (RAM)
