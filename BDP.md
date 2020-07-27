% Big Data Processing Infrastructures
% Saul Pierotti
% \today


# Part 1 - Prof. Daniele Cesini

---

# Introduction
* Prof. Cesini and Prof. Salomoni are both from the INFN-CNAF center in Bologna
* The CNAF is the computational center of the INFN, located in Bologna
	* It started as a facility for the analysis of data from bubble chambers
	* CNAF developped an managed the Italian research network, now managed by GARR
	* In 1990 CNAF realized the LHC Tier-1 datacenter in Bologna
	* One of the main actors in GRID worldwide computing
	* It offers CPU and sotrage resources to many INFN initiatives
* This course is about infrastructures, not about Big Data

# Big data
* Cell phone data were used in Pakistan to track and predict the spread of Dengue
* Google traffic suggests an optimal route to users according to current conditions
* Both of these applications process data from many sources, that come in a non-regular schedule
* They both need to quickly process huge amounts of data in real time
* The need to be able to quickly verify the validity of data
* We are currently producing around 40 Zb per year, and this number is in exponential increase
* Big data are characterized by Vs
	* Volume: typically several Tb ($10^{12}$) to Zb ($10^{21}$)
	* Velocity: data coming at high speed, with short time to react
		* We are in a real-time streaming more than in a batch processing scenario
	* Variety: data from different sources, in different formats
		* Data can be structured, semistructured or unstructured
		* A database table is structured
		* An xlm file is semi-structured
		* Text, images, audio files, video streams are unstructured
		* Big data tend to be mostly unstructured
	* Veracity: the degree to which data is trustworthy
		* Big data tend to involve datasets, problem spaces and environments that are difficult to trust
	* People are starting to add more Vs, but let's keep it simple and stick to these 4 Vs
	* Value: big data is about transforming a lot of data in something valuable
* The Gartner definition of Big Data: Big data is high-volume, high-velocity and/or high-varietyinformation assets that demand cost-effective, innovative forms of information processing that enable enhanced insight, decision making, and process automation
* Big data is not just about volume, but it definitely has a big volume
* Big Data is a lot of data, coming really fast, in many different formats and from many different sources
* The definition of Big data is not static, but it is relative to processing capabilities
* The Gartner hype cycle of emerging technologies: new technologies go through an innovation trigger, a peak of inflated expectations, a trough of disillusionment, and then finally enter the slope of enlightment and the plateau of productivity
* Big data is not reported in the last Gartner hype cycle, since it is NOT consider an emerging technology, but a prevalent aspect of many modern technologies
* Big data come from a variety of sources
	* Web data: the web browsing behaviour of customers, used for showing targeted ads
	* Text data: emails, documents uploaded, web forms
		* Typically key meanings are extracted and then used downstream for predictions and targeting
	* Time and geolocation data: deriving from GPS and WiFi data at the individual or aggregated level
		* Individual level: targeted advertising
		* Aggregated level: dimensioning and placing infrastrucutres
		* This type of data raises many privacy concerns
	* Smart grids and sensors data: data from cars, windmills, planes, turbines, oil pipes, and other apparati
		* They allow to improve performances and to diagnose problems early
		* A plane can produce 640 Tb of data per day
	* Social network data: analysis of the connections of a given user
		* These data can be used for targeting ads also on the basis of the social circle of the customer
* The value of data is not in the data themselves but in the value that arises from the combination of different pieces of information
* Big data can be an entirely unconventional source of data, like browsing behaviour in online shopping
* The speed of data feeds can transform old data in new data, by allowing a more in-depth analysis
* Most traditional data sources are structured, while Big Data tend to be unstructured
	* In traditional data every piece of information included is known ahead of time, comes in a specified format and occurs in a specified order
	* In Big Data there is no control over the source and the format of the data
	* Web logs are an example of semi-structured data: thelenght of the log is variable but it does follow an underlying logic
* The power of Big Data is in the analysis and the actions that you can take as a result of the analysis
	* The data themselves do not have any intrinsic value, they become valuable only when I am able to extract useful information from them
* The analysis of data can be descriptive, predictive, or prescriptive
	* A descriptive analysis looks at the past and tryes to extrapolate trends
	* A predictive analysis tryes to use past data to predict future behaviours
		* This is typically harder than a descriptive analysis!
	* A prescriptive analysis outputs recommendations according to past data
		* I can get a hint that a machine part is about to break
		* I can suggest news articles to a customer according to past browsing behaviour
* All these analysis approaches existed before Big Data, but Big Data improves the ability for precise future insight
* Segmentation: specific actors collect focused data
	* Banks can aggregate data on loans, mortgages, credit cards to calculate a credit score
	* Insurance companies can aggregate health data to predict the likelyhood of of health outcomes
* Churn prediction: a churn is the probability of a current customer to swtich to a competitor
	* A company may flag customers at the risk of churning using web data analytics and social media data
	* The company may propose targeted offers to avoid churning of those flagged customers
* Recommendation systems: they can be user-scpecific or general
	* User-specific recommendation: Amazon proposes recommended articles to buy, Spotify recommends the next song, and Netflix recommends the next movie
	* General trends: many platforms suggest products that have been generally sucsessfull
* Sentiment analysis: looking at the general public opinion on a topic or company
	* It typically uses data from social media
	* It can use aggregate data or individual data
	* It can use pattern recognition to detect the mood of a calling customer and direct it to the appropriate specialist
* Operational analytics: automate decisions
	* An airline reroutes coustomers automatically upon flight cancellation
* Social good, research, and personalized medicine: remote diagnosis and healt prevention with wearable devices
* Big Data is not only related to the commercial applications shown, but also to large-scale scientific experiments
	* The Square Kilometer Assay (SKA) is an international effort to build the word's largest radio telescope
	* The LHC produces 60 Pb of data per year
	* Climate and weather simulations require extensive data
	* Avionic simulations
	* Genome sequencing

# Computational challenge
* The challenge involves find a substring in a string
* Doing it brute force is really slow
* I can create an index once and then I can search every time much faster
	* Blast uses this approach
	* The BWA algorithm is another possibility
		* It is used for more similar sequences
		* It is faster when I have many reads to be aligned
* Using the right approach is much more effective than increasing computational power
* Read the literature: if you created your own tool, probably it is the wrong one
* If possible use open source code
* Avoid vendor lockin
* Use standards or de facto standards
* Think in advance about scalability
* A checksum is essential when we are moving data
	* It is a small string used to detect error in data transmission or storage
	* They are used to verify data integrity, not autenticity
	* It is possible to set an extended file attribute with the checksum (if the file system allows it)
* Files are moved compressed, moving uncompressed files is a crime

# From PC to datacenter
* 1 byte is composed of 8 bits (but we can also use 10 to make it easier)

## Processor
* A Central Processing Unit (CPU) is the electronic circuitry that execute the instructions that make up a computer program
* A CPU performs basic arithmeitc, logic, controlling and I/O operations specified by the instructions in a program
* A CPU is composed of an Arithmetic Logic Unit (ALU), processor registers and a control unit
	* The ALU performs arithmetic and logic operations
	* The registers supply operands to the ALU and store the result of ALU operations
	* The control unit controls the fetching of data from memory and coordinates the operations of ALU, registers and other components
* A multicore processor is an integrated circuit that has at least 2 processing units, called cores
	* Each core appears to the processor as a different CPU
	* A multicore processor executes ordinary CPU instructions, but multiple instructions can be run at the same time
	* It increases the overall speed compared to a single core for programs that support parallel computing
	* A socket is the physical matherboard processor, and it can have many physical and logical cores
* Hyper-threading is a propietary technology from Intel that represents each physical core as 2 logical cores at the software level
	* The OS sees a double number of cores with respect to the physical number actually present
	* It maximises the exploitation of the processor by running at the same time operations that are independent
		* An example can be doing an ALU operation and a logical operation at the same time
		* When a process is waiting for something the processor can run another process
	* It can improve performances but this depends on the application
	* It uses more die area (space on the silicon chip)
	* It can also degrade performance by trashing the cache
		* Memory is virtual in modern systems, in the sense that the address space used by applications does not refer to the physical memory adress
		* The MMU (memory management unit) translates the virtual adresses to physical adresses on the fly
		* Virtual memory is the virtual adress space, which can map to physical memory but also to disk
		* Memory is managed in chunks called pages by the OS
		* When a page is requested by an application, if its real location is not in memory it raise a page fault error
		* The OS then swaps the requested page in memory from the swap area of the disk
		* If there is no space in memory another page is swapped out to disk
		* If the memory is constantly full this swapping results in a lot of time spent moving data back and forth, degrading performances
* The `top` command on a Linux system shows the status of all the logical cores in the system
	* `wa` shows the time spent waiting for I/O
	* `load` average shows the number of processes waiting for enetering in CPU
		* It should be at most equal to the number of cores, otherwise we are in an overloading
* A good source of info for the system is `cat /proc/cpuinfo`
	* `flags` shows the capabilities of the processor (instructions)

## Memory
* Random Access Memory (RAM) is a device used for storing information for immediate use
* When talking about memory, in general we are referring to RAM
* RAM typicaly stores working data and machine code
* We typically have a memory hierarchy on a PC
	* The first-tier memory is the CPU register
	* L1, L2 and L3 cache in the processor
		* L1 is subdivided in L1i (instructions) and L1d (data)
		* L3 is shared among cores (in some cases), while L1 and L2 are core-specific
		* I have 128 KiB of L1i and 128 KiB of L1d cache, 1 MiB L2 and 8 MiB L3
	* Main system memory (RAM)
	* Swap as a last resort
* Different pieaces of memory have different latency
	* L1 has 4 cycles latency, 0.5 ns
	* L2 11 cycles, 7 ns
	* L3 39 cycles
	* RAM 107 cycles, 100 ns
* Data is transferred between pieces of memory in cache lines
	* It is a data chunk, typically 64 bytes
	* We can write code that optimizes the use of cache lines
		* Keep physically close in memory data which is aceessed together!
* Because of this latency differences, an $O(n)$ algorithm can perform better that a $O(1)$ if it cause less memory access
* A RAM disk is a portion of RAM used as a storage device
* Cache lines operate on 84 GB/s between register and L1, 60 GB/s between L1 and L2, 30 GB/s between L2 and L3 and 10 GB/s between L3 and RAM
* Registers typically use SRAM, while other caches use SRAM or DRAM and memory use DRAM
	* SRAM is static RAM, it does not need refreshing but it is still volatile
		* It is made with a bistable circuitry called flip-flop
		* It is more expensive than DRAM since it uses 6 transistors per bit (a flip-flop circuit!)
		* 1 Gb can cost 5000\$
	* DRAM needs refreshing and it is made with capacitors
		* Each bit is managed by one transistor and one capacitor
		* The transistor manages read and write operations on its capacitor
		* 1 Gb can cost 50\$
		* SDRAM is a DRAM which operates in sync with the clock
		* DDR is a type of SDRAM
* Memory status can be seen with `free`

# Network
* A computer network is an infrastructure that shares resources between nodes
* Network topology can affect reliability and throughput
	* Bus: everithing connected to the backbone
	* Star: everithing connected to a centrul node
	* Ring: each node connected to the ones at its sides
	* Mesh: each node is connected to an arbitrary number of nodes but guaranteeing that all nodes can be reached
	* Tree: hyerarchical
	* Fully connected network
* OSI (open system interconnection) model: a series of layers from physical to abstract
	* Layer 1, physiscal layer: concerns the raw bit transmission
		* It codes and decodes bits into the physical transmission protocol (voltage levels, frequencies, ...)
	* Layer 2, data link: node to node data transfer
		* It cacthes and corrects errors in layer 1 transmission
		* Itinitiates, mantains, and terminates node to node connections
		* The MAC is parto of this level
	* Layer 3, network layer: packets of data and transmission across networks
		* It splits the data in packets
		* It manages the route data to an address in the network
		* It can provide reliable data transfer, but not necessarily
	* Layer 4, transport layer: control data reliability
		* It re-transmits damaged packets
		* It includes TCP and UDP
	* Layer 5, session layer: ports and sessions
	* Layer 6, presentation layer: encryption and make the data usable
	* Layer 7, application layer: human-computer interaction layer, it interacts with applications and with the presentation layer
* OSI is a general networking model and reference framework
* The Internet does not strictly follow the OSI model, but it uses the internet protocol suite (TCP/IP)
* The TCP/IP model (not the TCP protocol!) is an alternative to OSI
	* It collapses OSI 7 to 5 in the application level and OSI 1 and 2 to the netwrok interface level
* LAN (local area network) are small and localised networks
	* They are present in houses (made by a router), universities, businesses
* WAN (wide area network) cover cities, nations, ecc.
	* It is made up of connected LANs
	* Routing a packet in a WAN means finding to whoch LAN it should go
	* ARPANET (US defense) was the first WAN and the first network to implement TCP/IP
* LHCone network: the WAN of the LHC
* Packets: organising data
	* The alternative is to transmit bit streams
	* It is a formatted list of bits of 10 bits to some kbs
	* They include control information like destination, source, checksums
	* The actual data transmitted is the payload
	* Increasing the payload increases speed at the cost of accuracy
* MTU (maximum transmission unit) is the size of the largest protocol data unit (PDU) that can be transmitted in a single network layer transaction
	* Larger MTU reduces overhead but can increase delay
	* It should be set so to respect the properties of the physical netwrok
* The MAC (media access control) address is a unique ID assigned to a NIC (network interface controller)
	* It is at OSI 2
	* It is used for communications within a netwrok segment
* The IP (internet protocol) address is a numerical label assigned to the machine
	* It is at layer OSI 3
	* IPv4 is a 32 bit number
	* To make it more human-readable, each byte is represented with a decimal number from 0 to 255
* The IP is subdivided into a subnet and a rest field using the CIDR notation or the subnet mask
	* The network prefix identifies the netwrok, while the rest field is host-specific
	* The CIDR notation is represented with a slash after the IP that says the number of bits to be used for the subnet
		* `192.168.1.1/24` means that the first 24 bits of the 32 total (`192.168.1`) are the subnet, while `1` is the rest field
	* The subnet mask (255.255.255.0) means that the first 3 bytes are the subnet while the last one is the rest field
		* The subnet is obtained with a bitwise AND between IP and subnet mask
* IPv4 uses private adresses, that do not to be globally unique
	* They are not exposed to the internet
	* The private address is translated to/from a global address with NAT (network adress translation)
* There are 3 non-overlapping adrress ranges reserved for private use
	* 24 bit block: CIDR 10.0.0.0/8
		* 8 bits is the subnet so 24 bits (8-32) is the rest field
	* 20 bit block: CIDR 172.16.0.0/12
	* 16 bit block: CIDR 192.168.0.0/16
		* 8 bit block: CIDR 192.168.0.0/24
* IPv6 has a 128 bit address space
	* Actually it is much different from IPv4 in terms of routing
	* Its size allows to reserve large address blocks for specific use
	* The unique local address (ULA) is reserved for local use
		* It is fc00::/7
* `ifconfig` can be used to configure the network interface
* The loopback network device: a connection to the same machine
	* It is entirely managed by the OS and does not send any packet to network devices
	* It is assigned to the block 127.0.0.0/8 in IPv4
	* In practice it is used almost always 127.0.0.1
	* `localhost` is mapped to 127.0.0.1
	* It is used for diagnostic and by applications to reach resources on the same machine
* DNS is a decentralised mapping system between IP addresses and mnemonic names 
* A network protocol is a set of rules for exchanging packets over a network
	* In a protocol stack each protocol uses services from the one below it
	* HTTP runs over TCP which runs over IP
* There are various kinds of bandwith
	* Goodput is the actual data transmitted
	* Channel bandwith includes also the overhead control information
* Latency is measured as end-to-end delay (OWD) or round-trip-time (RTT)
	* It can be assessed with `ping`
	* RTT is usually 2*OWD, but not necessarily (upload and download can difffer)
	* Latency cannot be smaller than what the speed of light requires!
* Network adapters are physical devices that connects a computer to a network7
	* They can be part of the motherboard or can be plugged in as expansion cards
	* They implement OSI 1 and 2
	* Netwrok adapters are Ethernet, WiFi, Fiber Channel
	* There are also high-performace adapters used for high-performance computing like Omnipath and Infiniband
		* Infiniband (Melanox) and Omnipath (Intel) are high bandwith and low latency network interfaces
* Hub: it broadcast the same packet to all the ports
* Switch: delivers a packet to a specific machine
	* It knows the MAC of all the devices attached to it 
	* It works at OSI2 (and in some case at OSI3)
	* It does not increase significantly network response times
* Router: delivers a packet to an IP address
	* It can route to other LANs
	* It works at OSI3
* Top-of-the-rack switching: a switch that delievers packets to a rack of servers
	* Usually there is also a switch that delivers to the right rack

# Computing Infrastructures
* A computing farm is a collection of servers and it can have millions of cores
	* Network devices manage communication between servers and the interaction with users
* Intel Xeon is used in datacenters since it is reliable and can work continuously
* The link between sockets in the same motherboard is called qlink
* Servers are organised in hot islands which are separated by a cooling system
* A computing farm is usually shared among paying customers
	* The resources must be allocated effciently among users
	* The batch scheduler manages resource access
* A batch system takes care of scheduling non-interactive jobs
	* There are many batch systems: HTCondor, OpenLava, LSF, ...
	* It dynamically allocates jobs so to maximise cluster use, minimise latency and respect fairshare on a time window
	* It provides a single point of control for jobs submitted to the CPU farm
* Jobs are composed of
	* Job type
	* Prologue: initial checks
	* Input sandbox: the list of needed files
	* Requirements: the hardware required
	* Executable: the actual code to run
	* where stdout/stderr should be directed
	* Output sandbox: the files that need to be produced
	* Epilogue: final cleanup, file uploads, updates, ...
	* Error recovery: what to do if the job fails
* A job can be a single batch job that occupyies a single slot and it is executed in one core
* A DAG workfolow is a series of jobs dependent from each other described by a directed acyclic graph
	* It is essentially a pipeline
* A collection of jobs can be run in parallel
* A parallel job needs more than 1 core to run
* Reservation: the batch scheduler can reserve cores for 1 job that is waiting for something to be executed
	* This is typical of parallel jobs that are waiting for enough cores to be available
* Backfill: while the reserved core are idle they can be used by other jobs
	* Only jobs that will finish before the job that reserved the cores will start are permitted

# Storage
* The performance of a storage device is described in terms of bandwith and IOPS
	* The bandwith is the data transfer speed
	* The IOPS is the number of I/O operations per second
		* It is importnat when operating on small files
* SSDs use NAND technology, it is much slower than RAM but non-volatile
	* It can withstand a limited number of write cycles
	* NAND SSDs use NAND logical gates
	* The NAND used in USB drives tend to be less performant, cheaper and less durable than the one used in SSDs
	* Speed is 400/500 MB/s, 100k/400k IOPS
	* Capacity 500 GB
	* The biggest advantage of SSDs is in terms of IOPS
* Hard disks are slow since they have moving parts
	* Speed is 100/150 Mb and 100/200 IOPS
	* Capacity 8 TB
	* They have spinning disks and a moving head
* Tape cartridge are expensive since they require an infrastructure (tape library) but really scalable
	* Speed is 250 MB/s, sequential access (no IOPS)
	* Capacity 8.5 TB
* Data maintainance is a huge responsibility, since it could be impossible to recreate lost data
* RAID (Redundant Array of Independent Disks) systems allow to virtualize data storage
* RAID0: file striping at the block level
	* A single file is stripped into several drives
	* I collect n physical disks into 1 virtual disk
	* I get higher performances but no redundancy
	* Losing only 1 disk means losing all the data
* RAID1: file mirroring
	* Performances can imporove for reading
	* 2 disk that operate as 1, mirroring theyr contents
* RAID2 is rarely used and involces stripping at the bit level
	* It uses an Hamming code for error correction
* RAID3 is rarely used and involces stripping at the byte level with a parity disk
	* A parity disk contains parity bits for each block, that are used in error correction
	* It requires the rotation of disks to be in sync!
* RAID4: block-level stripping with parity disk
* RAID5: block-level stripping with distributed parity
	* In each disk I have all the blocks but 1 plus the parity of the missing block
	* It requires at least 3 disks
	* It is similar to RAID0 in term of performances (but a little bit less), but tolerant to the loss of an entire disk
	* It is more reliable of RAID0 because of parity, but also less performant
* RAID6: block-level stripping with double distributed parity
	* It is similar to RAID5 but it uses 2 parity blocks
	* It can tolarete the failure of 2 disks
	* It requires a minimum of 4 disks
* A file system controls how data are stored and retrieved in the physical medium
	* It can suppor file metadata like owner, permissions, access time
* POSIX (Portable Operating System Interface) is a family of standards for maintaining compatibility between OS
* A POSIX filesystem basically is one that supports open operations
* Cables are important, especially for DAS (direct access storage) systems
* A DAS system does not incorporate any network capability
* A JBOD (just a bunch of disks) is a container containing disks that can be plugged into a server
* A NAS (network access storage) is a storage device exposed to the network
	* It has file level access for external clients
	* It uses protocols like NFS and SAMBA
* The storage area network (SAN) is a dedicated network for storage access at the block level
	* I am not exposing the file system, but the disk itself
* The SAN is composed of an host layer, a farbric layer and Storage layer
	* The host layer is composed of servers that allow access to the SAN
	* The gabric layer is composed of cables, routers, switches
	* The storage layer is composed of the storage devices
		* Every partition of every storage device is identified by a logic unit number (LUN)
* Important data are backed up frequently and possibly moved to a different geographical location
* A parallel filesystem is a single filesystem across multiple storage devices
	* It usually supports mutliple clients (thousands of them!)
	* It is built on a SAN, with block level access
	* It maintaines metadata servers with information about the location of the blocks for each file and their metadata
* Metadata are essential and cannot be lost: metadata servers have a lot of redundancy
* A distibuted file system is built on a system with file-level access
	* It is built on top of the file systems of the disks!
	* They are typically slower than parallel file systems
* The tape area network (TAN) is a subsection of a SAN dedicated to tape devices
	* Tapes are organized in libraries containing tape drives and robotic arms that move the tape cartridges into the drives
	* A tape library can have 85 PB capacity
* Storage is organised in tiers according to their QoS
	* Tier 1 storage is used for hot data (frequently used)
		* It is composed of large RAID systems and SSDs 
	* Tier 2 is used for warm data
		* It is mainly old disks and small RAIDs
	* Tier 3 is used for cold data like backups and rarely accessed data
		* It is mainly tape storage
* Moving a file to an higher QoS is call recall, moving it to a lower one migration
* Tape storage is extremely safe: I can put the cartridge in a safe box and it is inaccesible
* Nowadays datacenters are adopting the HyperConverged architecture
	* Storage and computing happens on the same machines, no separate areas

# Cloud Computing
* Cloud computing deals with supplying information and communication technologies as a service
* It enables uniquitous access to shared pools of configurable system resources and higer level services that can be rapidly provisioned with minimal management effort, often over the internet
* It is similar to a public utility in that achieves economy of scale and coherence
* The core characteristics are that it is self-service and on-demand, network based
* Physical resources are pooled and the user has no control over them
* It uses a pay-per-use model
* It is not the same as virtualization but it can employ virtualization to pool physical resources
* The offer is elastic and can be adapted to user needs
* The infrastructure has a teorethical infinite capacity, but you need infinite money to use it!
* The model is focused on the concept of service, without the need of thinking about the underlying physical infrastructure
* Infrastructure as a service (IaaS): the customer receives a machine with an OS
	* It can provide storage, computational and network services and it is often virtualized
* Platform as a service (PaaS): the customer manages data and software, but no direct access to the OS
	* I can ask for a HTC-Condor cluster already functional, a parallel file system, an SQL database
* Software as a service (SaaS): pre-formed environment entirely managed by the vendor
	* Gmail infrastrucutre for managing the email of a company
* At the end, what matters for the user is the application: don't focus so much on the implementation!
* The cloud paradigm has 3 main dimensions: service model (Iaas, PaaS, SaaS), deployment and isolation
* Deployment refers to where the services are distributed and it can be public, hybrid or private
	* A private cloud is accessible only to insidersa and it rarely has infinite resources
	* A public cloud is AWS, which can be assumed as infinite
	* An hybrid system is a private system that redirects peak requests to a public system
	* I could also decide to use a private system for sensitive data and a public cloud for non-sensitive data
* Isolation concerns how I isolate the servies offered to different customers
	* A dedicated cloud is dedicated to a scope (es. Bioinformatics)
	* A multi-tenant cloud is multi-purpose and is used by customers with different goals
	* I can also consider a tenant as a group of customers (es. research group), that payed for a specifc QoS
* The interaction of an end user with the cloud (es a Facebook user) must be
	* Easy to access without any specific technology
	* Private and secure
	* It must provide means for authentication
* Migrating an application to the cloud can be motivated by reduction of costs, business agility and savings on management
* The choice of a public or private cloud can be influenced by the cost of WAN traffic, security concerns and integration with pre-existing applications
* Migrating to a SaaS is not actually a migration but a chango of application
* Web hosting is one of the most common cloud use cases
* Public clouds can be adapted much quicker to the demand!
* Multi-tiered application are organized into a data management tier, a business logic tier and a presentation tier
	* If well designed it is possible to migrate the tiers independently to the cloud
* A stateless service does not store the state (non-interactive web server)
* A stateful service stores information about user interaction (a shopping cart
	* It cannot be replicated easily!
* A cloud-friendly application is stateless and distributed
	* If there is a rise in requests I can just duplicate the system and create a new instance
* Cloud-friendly applications are like cattle: I can easily replace them when needed
* Legacy applications are like pets: I cannot replicate them and I need to take care of them
* The reduction of costs in the cloud is due to economy of scale and less requirements for management
	* Cooling systems are cheaper if used for huge datacenters
	* Lower hardware costs due to the number of units bought
* The cloud democratizes resource access to small actors, since it make the resources more finely divideable
* SaaS applications provide ubiquitous access to resources from any device without specific software needed
* Cloud risks: security, privacy, vendor lock-in, data loss
	* In the terms of service for standard accounts there is no guarantee of continuity, reliability, ecc
	* In many case cloud services are not completely mature

# Virtualization
* Virtualizing means creating a virtual version of a physical resource through an abstraction layer that hides the underlying implementation
* Virtual machine are hardware-independent and their resource usage can be dynamically adapted
* Thanks to virtualization I can consolidate the services provided by many servers
* Applications are sandboxed in a virtual environment
* Virtual applications can be provisioned on demand
* Virtualization is vulberable to bugs and hacking, since many different hosts and OS are co-existing in the same hardware
	* A VM can have unauthorized acces to data of another VM
	* Some hypervisors work directly at the level of the hardware: everything can be compromised
* Performances in a virtual environment can be worse due to the overhead for the physical host
	* This is true particularly for I/O operations
* The cloud can be provised with or without virtualization
* Provisioning of VMs is NOT cloud computing if it does not respect the self-service, on-demand, network-based, elastic offer and pay-per-use paradigms

# Databases
* Big data are typically stored in relational or non-relational databases
	* Non-relational databases require little coding skills
		* They include NoSQL databases like MongoDB
	* Relational databases are massively parallel systems
		* They typically require data scientists
* There is a huge amount of software in the big data ecosystem

## MapReduce
* MapReduce is an algorithm developped by Google for parallel and decentralized processing and generation of big data
	* It usually uses a distributed filesystem like Hadoop
* It is based on the Map and Reduce actions
	* Map: convert a set of data into another, described by key/value tuples
		* I can take a document and form a dictionary with single words as keys and their count in the document as value
	* Reduce: aggregate the data from a set of tuples
		* I take several dictionaries from different documents and count the total word occurrence

## Hadoop
* Apache Hadoop is an open-source software ecosystem for big data analysis and storage
	* It is designed to scale well from a single server to thousands
	* It is highly fault tolerant
	* It is typically run on low-grade hardware, but it is highly reliable because of the software-level failure handling
	* New nodes can be added quickly without changing configurations
	* It does not require any schema, it can accept any kind of data
	* When a node fails the system just redirects the load on the remaining nodes, without halting
* Hadoop is composed of
	* Hadoop Common: a series of common utilities that support the other modules
	* Hadoop Distributed File System (HDFS)
	* Hadoop YARN: framework for job scheduling and resource management
	* Hadoop MapReduce: a YARN-bases system for parallel processing based on the MapReduce approach
	* Hadoop Ozone: object store
	* Hadoop Submarine: machine learning engine
* The Hadoop Distributed File System (HDFS) is the core component of the Hadoop ecosystem
	* It abstracts resources and allows to see the whole HDFS as a single unit
	* It stores data in the various nodes and mantains metadata
	* It is composed of 2 core components: NameNode and DataNode
	* NameNode is the metadata server: high computational requirements but low storage requirements
	* DataNode: commodity hardware with more storage resources
	* There is typically only 1 NameNode and many DataNode
* Writing in an Hadoop cluster requires 2 essential pieces of information to be submitted with the data: block size and replication (number of copies of the block that I want)
	* Typically a block size of 64 or 128 Mb and a replication of 3 are used
	* The client sends the request to the NameNode, which returns a sorted list of DataNodes in order of distance from the client
	* The client sends the data only to the first DataNode
	* The first DataNode sends to the second and so on for the desired replication level
	* All the DataNode send a confirmation for finished writing to the NameNode
	* When all the blocks have been written the NameNode stores the file metadata
	* The NameNode returns a success message to the client
* Reading data from an Hadoop cluster
	* The client request a file to the NameNode
	* The NameNode returns a list of blocks and of DataNodes having them
	* The client retrieves the blocks from the respective DataNodes
* Node failure in Hadoop is handled by the NameNode
	* The DataNodes every 3 seconds send and HEARTBEAT message to the NameNode, signaling their presence
	* If the NameNode does not receive the HEARTBEAT from a DataNode (because it is dead or there is a network failure) it considers it dead
* Network failure handling in Hadoop
	* Whenever data is sent the receiver returns an ACK message
	* If the ACK message is not received after several trials the sender assumes the receiver to be dead
* Corrupted data in Hadoop
	* Data always include a checksum when it is sent and when it is stored
	* DataNodes periodically send a BLOCKREPORT to the NameNode, a list of all the blocks in the node
		* Before sending the BLOCKREPORT a DataNode checks all the block checksums
		* If a block is corrupted it is not sent to the NameNode, that assumes the missing one to be corrupted
* The NameNode always mantains 2 essential tables: a list of blocks and a list of DataNodes
* When a DataNode is dead or assumed dead, it is skept for all transactions both by client and NameNode
	* If it is so the data will not reach the desired replication, but the NameNode will subsequently instruct the DataNodes to copy data from each other accordingly
* In order to be as resilient as possible, block replicas are kept at most as 1 per datanode and 2 per server rack, if possible
	* It is also possible to specify a custom placemnt algorithm
* YARN performs allocates resources and schedules jobs in the Hadoop cluster
* It is composed of 2 major components: ResourceManager and NodeManager
* The ResourceManager is the central node of the cluster
	* It receives requests and dispatches them to the relevant NodeManagers
* The NodeManagers are installed onto each DataNode and manages task execution of that node
* ApplicationManagers accept job submission and forwards them to the respective ApplicationMaster on the DataNode
* Hadoop MapReduce is the core processing component of the ecosystem
	* It is a software framework for writing applications that process large datasets using distributed and parallel algorithms in an Hadoop environment

## SQL
* It is a relational DBMS based on tables
* It works with a specific schema
* It uses the powerfull SQL query language
* Implementations are MySQL, Oracle, Sqlite, Postgres
* It is typically commercially supported
* It focuses mostly on consistency: the database of a bank
	* We can say that it focuses on the ACID properties: atomicity, consistency, isolation, durability
* Scalability is vertical

## NoSQL
* In is non-relational and document-based
* It can consist in key-value pairs, graphs, wide-columns
* The schema is flexible and it can also host unstructured data
* Scalability is horizontal: I can just increase the number of servers in the pool
* It uses the non-standard UnQL query language (unstructured query)
* Implementations are MongoDB, Cassandra
* It is typically supported by the community
* It focuses on availability: it does everything possible to remain operational also in case of errors
* Consistency is eventual: it is not guaranteed at the end of each transaction but eventually it is restored when there is time available for the operation
* Apache Cassandra is open-source, distributed
	* There is no central node, so no single point of failure
	* It works with wide-columns
	* It was initially developped at Facebook
	* It supports Hadoop integration and MapReduce
	* It uses the novel query language CQL
* Apache Kafka is a distributed streaming platform

# Parallel computing
* The distributed infrastructures we saw until now were localised in the same WAN
* High throughput computing (HTC) I want to maximise the number of jobs executed, not speed up the single job
* High performance computing (HPC): I want to speed up the execution time of the single jobs
* FLOP: number of floating poin operations per second

# HTC
* HTC infrastructures are PC clusters, server clusters, distributed systems and grids
* A Grid is an hardware and software infrastructure that provides inexpensive access to high-end computational capabilities
	* It is NOT subject to centralised control
	* Uses standard and general-purpose interfaces
	* Delivers non-trivial QoS
* The user of a Grid is a virtual organization
	* It is a set of individuals that share the resources under certain rules
	* Sharing of resources is highly controlled and well-defined
	* The owner of the individual resources decides who can access them
* 95% of the Grid is agreement on protocols between participating institutions
* There is no Grid owner and the network is distributed: I do not know which machine is processing my data
* Grids can be based on supercomputers, servers, or volunteers that share desktop PC power
* Grids are really complex, and they often fail
* The Grid implements a single sign on policy (one access system grants all the resources available)
* The Grid should allow for delegation (automatic access by programs)
* The X509 certificate is used for signing into a Grid
	* It contains the Public key of the owner, its identity
	* It is sgned by a certification authority
* The certification signs the authorization for the user
* The user can in turn sign a proxy authorization for allowing delegation
* Each job on the Grid is identified by an URL containing the address of the server who accepted it and a random string

# HPC
* Some glossary
	* GFLOPs: billions of floating point operations per second
	* TDP: thermal design power, it is the maximum amount of heat that the cooling system must be able to dissipate in typical operations
* The max GFLOP of a system can be calculated from the number of sockets, cores per socket, clock frequency and FLOPs per cycle
* The first machines for HPC were vector machines
	* They are contrapposed to the currently used scalar machine for the fact that they could operate directly on vectors with their instruction set
	* They were using single powerfull processors (small for now!)
* CRAY-1 (1976) was one of the first vector machines
	* It was able of 80 MFLOPs in scalar operations and 160/250 MFLOPs in vecotr operations
	* It was consuming 115 kW for operation + 330 kW for refrigeration!
* CRAY-XMP (1982 and 1984) had first 2 and then 4 processors and was capable of 2*200 MFLOPs (800 MFLOPs with 4 processors)
* CRAY-2 (1985) had 4 processor and was able of 1.9 GFLOPs
* Subsequently in the 80s there was a shift for vector machines to massively parallel processors (MPP)
	* They used many standard processors connected in the same machine
* In MPP processors need to communicate, since they are operating together on a single job
	* There are low-latency connections between them and specialized netwroks
* In time many dedicated MPP supercomputers were produced
* In 1985 Thinking Machines produced the CM-1, and then the CM-200 and CM-5
	* CM-200 had 65536 1-bit CPUs and was capable of 40 GFLOPs
* Intel Paragon was lauched in 1993 and had 4000 Intel i860 RISC microprocessors
	* It was capable of 184 GFLOPs
* ASCI Red MPP (1997) was capable of 1.4 TFLOPs and it was the first supercomputer above 1 TFLOP
* IBM BlueGene was designed as multiple SoCs (system on a chip) and was able of 20 PFLOPs
	* It was focused on low power consumption
* A cluster is a paralle computer system made of an integrated collection of independent nodes (each of them capable of autonomous operation) and derived from products developped for other stand-alone purposes
* It is possible to use a cluster of commercial-grade servers for HPC
	* In this case I need a really low-latency network to make them cooperate effectively
* Most HPC systems are built for the industry, not for research
* Main applications of HPCs are astronomy, molecular dynamics, earth simulations, fluid dynamics, brain simulations, general relativity calculations
* The speedup of an application when it runs in parallel on P processors is the ratio among the running time on a sequential system and that on the parallel system
	* If the speedup is equal to the number of processors it means that there is no overhead for the parallism: perfect linear speedup
* The efficiency of a parallel system is the ratio among the speedup and the number of processors
	* It is 1 in case of perfect linear speedup
* In rare cases the speedup can be superlinear, usually because of memory caching
* Amdahl's law predicts the speedup of a computation by assuming linear speedup
	* It leaves the serial processing part of the job untouched while it divides the parallel computation by the number of nodes
	* The maximum possible speedup is $S= 1/\alpha$ where $\alpha$ is the serial fraction of the computation
* HPC systems can use shared memory (RAM) in order to share information among threads and processes
	* Processes can run in the same or different processors when using shared memory
	* This is an efficient mean for sharing information among processes
* In uniform memory access (UMA) all the processors share uniformly the same RAM
* In non-uniform memory access (NUMA) the memory access time depends on the location of the memory relatively to the processor
* When I am using shared memory I need to ensure that also the CPU caches are syncronised!
* A Race condition is when the output of a parallel program changes by changing the order of execution of its threads, and it is generally bad
* The NUMA API is used for setting shared memory allocation policies
	* libnuma can be used for setting up a NUMA environment
* OpenMP is another API used for writing multithreaded applications
	* It shares variables among threads and greatly simplifies parallel programming in C/C++/Fortran
	* It can cause a Race condition when common variables are unintentianally introduced in the threads
	* I can use synchronization to protect data conflicts, but it is computationally expensive
* Distributed memory refers to a multiprocessor system where each CPU has its own memory
	* In this case the communication among threads in mediated by explicit send/receive calls
	* Each CPU can only operate on local data
* MPI is an API used for creating distributed HPC
	* Its core is representedby the functions `MPI_Send` and `MPI_Recv`
	* The data to be sent or received is blocked, meaning that the function returns only when the data can be safely used
	* The reduction operation can be used for summarising a set of numbers ot a smaller set of numbers
		* It takes the input from tje distributed processes and then places the result only in the root process
* Hardware coprocessors can be used for accelerating FLOPS
* Coprocessors are not a new idea: in 1980 the Intel 8087 was on of the first floating point coprocessors
	* The 8087 was the first coprocessor to use the x87 instruction set
	* The x87 was adopting the important IEE74 standard for floating point operations
* Vector coprocessors in time were absorbed into CPUs and now are a main part of every CPU
* The GPU is one of the most used coprocessors
* In the 2006 CUDA was born: it is a parallel computing platform for performing general computation in GPU
* A GPU is driven by a CPU that manages the code to be executed on GPUs, the memory of the GPU and the movements between CPU and GPU
* A modern siliconn chip contains integrated components: in the same chip I can have CPU, GPU, chaches
* HPC applications can be bounded by computing or by bandwidth
* When comparing performances of CPU and GPU, be sure that the applications used for the comparison are optimized for both CPU and GPU and that the algorithm is state of the art!
* When you see claims of 100+ speedup due to GPU, be suspicious!

# Containers
* A container is a framework used on top of other infrastructures, typically a cloud
* Virtualization is the creation of a virtual version of something
	* It can be anything: storage, network device, OS, ...
	* A virtual machine is a virtual copy of a real machine
* KVM is a linux kernel module used for virtualization
* The host is also called hypervisor
* A VM includes a guest OS, so it has a lot of overhead
* A (docker) container does not include an OS, it is based on the host OS
	* It operates at the application level
	* It has the same pros without many of the cons of VMs
	* It emulates binaries and libraries needed for the application
	* It is an extended version of `chroot`
* The docker engine manages resources for the different containers
* They make software deployment (distribution) much easier
	* I can create a container with an application and its dependecies and just distribute it
* They can be compared to shipping containers for goods
* In order to execute a container I just need the right kernel, without worrying about libraries and binaries
	* I also need the docker engine!
* Docker is a software used to manage and create containers
	* It provides also a git-like versioning system
	* You build a container image and push it to a container image repository
	* From another host I pull the container image and just run
		* Need to have the same kernel!
* There are many container engines, but they are usually compatible
	* You can build with a manager and then run with another

# Low power devices
* Exascale computing with traditional means requires a nuclear reactor for power!
* Europe is leader in the production of SoCs and low-power devices
* ARM was born in the UK, but now it is owned by a japanese firm
	* It is the main SoC producer

# Internet of Things (IoT)
* The IoT is the network of connected physical devices through their electronic components
* Each 'Thing' can be identified via its MAC address

# Part 2 - Prof. Salomoni

---

# Introduction
* This module focuses on topics beyond the IaaS model and it is mostly hands on
* The main topics are: cloud storage, Docker containers, authentication and authorization for cloud services, automation for cloud applications
* Professor is also a physicist from INFN, graduated from UniBo
* INFN centers are linked by the high speed connections provided by the GARR network
* The cloud is useful since it allows to optimize resource usage in presence of elastic demand
* The cloud should be accessible on demand as a self-service
* The access is network-based, relies on resource sharing and it is assumed to be infinitely elastic
* It has a pay-per-use model
* Above the IaaS/PaaS/SaaS axis there is the isolation model dimension and the deployment model dimension


* Docker containers are lighter than traditional VMs since they include only what is different between the host and the guest so to be able to run applications on the guest
