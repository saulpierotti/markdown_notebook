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
* Different pieaces of memory have different latencies
	* L1 has a 4 cycles latency, 0.5 ns
	* L2 11 cycles, 7 ns
	* L3 39 cycles
	* RAM 107 cycles, 100 ns
* Because of this latency differences, an $O(n)$ algorithm can perform better that a $O(1)$ if it cause less memory access event
* The memory bandwidth is the rate at which data can be read or stored in a semiconductor memory by a processor
	* It is usually expressed in bytes per second
	* The total bandwidth is the product of clock frequency, number of transfers per cycle, memory bus width, and number of memory interfaces
	* Double Data Rate (DDR) RAM pieces can perform 2 transfers per clock cycle
	* The memory bus has typically a width of 64 bits (also called a line)
	* Modern PCs have 2 memory interfaces, so they effectively have a 128 bits line width
* Data is transferred between pieces of memory in cache lines
	* A cache line is a data chunk, typically of 64 bits
	* We can write code that optimizes the use of cache lines by keeping physically close in memory data which is frequently accessed together
* Cache lines operate on 84 GB/s between register and L1, 60 GB/s between L1 and L2, 30 GB/s between L2 and L3 and 10 GB/s between L3 and RAM
* A RAM disk is a portion of RAM used as a storage device
	* It is much faster than a conventional disk, but it is not persistent if the RAM is not arranged so to have a standby battery source
* Modern PCs extend RAM capacity by using virtual memory
	* A virtual memory space is a part of an hard disk that it is used as an extension of the physical RAM
	* It is also called swap space
	* The data is typically stored in a dynamic paging file on the hard disk
	* Overuse of swap space can trash performances, since an hard disk is much slower than real RAM
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
* The memory status of a Linux system can be seen with the `free` command

## Network
* A computer network is an infrastructure that shares resources between nodes
* Data transmission between nodes is supported over data links consisting of a physical medium
* A network node is a network computer device that originates, routes or terminates data communication
* Nodes are generally identified by network addresses
* Network topology can affect reliability and throughput of a network
	* The more connected a network is, the more reliable, but also the more expensive to build and maintain it is
	* Bus: everithing connected to the backbone
	* Star: everithing connected to a centrul node
	* Ring: each node connected to the ones at its sides
	* Mesh: each node is connected to an arbitrary number of nodes but guaranteeing that all nodes can be reached
	* Tree: hyerarchical organization
	* Fully connected network
* The OSI (open system interconnection) model: a conceptual model that characterizes and standardizes communication in computer systems without regard to its internal structure or technology
	* Layer 1, physiscal layer: concerns the raw bit transmission
		* It codes and decodes bits into the physical transmission protocol (voltage levels, frequencies, ...)
		* The data transmitted is unstructured: it is just bits
	* Layer 2, data link: node to node data transfer
		* It catches and corrects errors in layer 1 transmission
		* It initiates, mantains, and terminates node to node connections
		* The Medium Access Control (MAC) layes is part of this level
			* It is responsble for controlling how network devices gain access to a medium and to the permission for transmitting data
		* The Logical Link Control (LLC) layer catches and corrects errors in layer 1
	* Layer 3, network layer: packets of data and transmission across networks
		* It splits the data in packets
		* It manages the route to an address in the network for data packets to follow
		* It can provide reliable data transfer, but not necessarily
		* It may (or not) report on delivery errors
	* Layer 4, transport layer: control data reliability
		* It re-transmits damaged packets and ackowledges successfull data transmission
		* It segments the message from the application layer and de-segments it for the application layer on the receiving end
		* There are 4 classes of transport protocols from class 0 (fewest features) to class 4 (for unreliable network such as the Internet)
		* Class 4 transport protocols are close to TCP
	* Layer 5, session layer: manages ports and sessions, and maintains connections
	* Layer 6, presentation layer: it ensures that the data is in a usable format
		* If needed, it performs encryption and decryption
	* Layer 7, application layer: human-computer interaction layer, it interacts with applications and with the presentation layer
		* It is the interface that an application uses for interacting with the network
* OSI is a general networking model and reference framework
* The Internet does not strictly follow the OSI model, but it uses the internet protocol suite (TCP/IP)
* The TCP/IP model (not the TCP protocol!) is an alternative to OSI
	* It is called TCP/IP because it is based on the TCP protocol and on the IP protocol
	* It collapses OSI 7 to 5 in the application level and OSI 1 and 2 in the netwrok interface level
* LANs (Local Area Networks) are small and localised networks
	* They are present in houses (made by a router), universities, businesses
	* They are controlled and managed in-house by the organization that deploys them
	* They are typically fast and trusted
* WANs (Wide Area Networks) cover cities, nations, and the whole world
	* They are made up of connected LANs
	* Routing a packet in a WAN means finding to which LAN it should go
	* The Advanced Research Projects Agency Network (ARPANET, US defense) was the first WAN and the first network to implement TCP/IP
* The LHCone network is the WAN of the LHC, that connects LHC tier 1, 2, and 3 sites
* Computer communication links that do not support data packets work by transmitting bit streams
* The wast majority of computer networks transfers data in packets
	* A packet is a formatted unit of data
	* It is a list of bits, a few 10 byets to some kylobytes long, carried by a packed switched network
	* A message that does not fit in a packet is divided in multiple packets and then re-assembled at the destination
* A packet is composed of a payload and control information
	* The payload is the actual data that needs to be transmitted trough the network
	* The control information provides the data that the network needs for correct shipment of the packet: source, destination, error detection code, sequencing information
	* Increasing the payload proportion in a packet increases the transmission speed at the cost of accuracy
* The MTU (maximum transmission unit) is the size of the largest protocol data unit (PDU) that can be transmitted in a single network layer transaction
	* It is related (but not equal, there is control information!) to the maximum frame size that can be transported by the data link layer
	* A larger MTU is related to a reduced overhead while a smaller MTU can reduce network delay
	* It should be set so to respect the properties of the physical network and not exceed its capabilities
* The MAC (Media Access Control) address is a unique ID assigned to a NIC (Network Interface Controller) for use as a network address in a given network segment
	* It is used in most of the IEEE802 technologies such as Ethernet, WiFi, Bluetooth
	* It is at the medium access control protocol sublayer of the data link layer (OSI layer 2)
	* A MAC address is composed of 6 groups of 2 hexadecimal digits separated by hyphens, colons, or without a separator
	* It is assigned primarily by the device manufacturer and physically stored in a read-only memory or in the firmware of the device (burned-in address)
* The IP (internet protocol) address is a numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication
	* It serves as an identifier of an host on a network and for the routing of packets
	* IPv4 defines an IP address as a 32 bit number
	* To make the IP address more human-readable, each byte is usually represented with a decimal number from 0 to 255 ($2^8 = 256$ possible states of a byte)
* The IP is subdivided into a network prefix (subnet) and a rest field (host identifier)
	* The network prefix is represented by a variable number of higer-order bits
	* How many bits belong to the network prefix can be specified using the CIDR notation or a subnet mask
	* The CIDR notation is represented with a slash after the IP address that specifies the number of bits to be used for the subnet
		* `192.168.1.1/24` means that the first 24 bits of the 32 total (the first 3 of 4 bytes, `192.168.1`) are the subnet, while `1` is the rest field
	* A subnet mask is used in a logic AND operation against the IP address for obtaining the subnet, and in a NAND operation for obtaining the rest field
		* A subnet mask of `255.255.255.0` means that the first 3 bytes belong to the subnet while the last byte forms the rest field
* The early design of the IP envisioned global end-to-end connectivity among all the Internet hosts
	* This required all the addresses to be globally unique
* Subsequently, with the development of private networks, it was realised that private addresses for each device needed to be unique only inside the LAN, while maintaining a gloablly unique public address for the LAN router
	* Computer that are not directly connected to the Internet use a NAT (Network Address Translation) service that translates their private IP to/from the public IP of the router
* There are 3 non-overlapping address ranges reserved for private use
	* 24 bit block: CIDR 10.0.0.0/8
		* The first byte (10) is the subnet, while the 3 following bytes compose the host identifier
	* 20 bit block: CIDR 172.16.0.0/12
		* The first byte and part of the second form the subnet (172.16 to 172.31)
	* 16 bit block: CIDR 192.168.0.0/16
		* The first 2 bytes (192.168) form the subnet, while the 2 following bytes compose the host identifier
	* 8 bit block: CIDR 192.168.0.0/24
* In the version 6 of the Internet protocol (IPv6) the address space was increased to 128 bits
	* The address space is not the only difference between IPv4 and IPv6, they are much different in terms of routing
	* The magnitude of the IPv6 address space is deemed sufficient for the foreseeable future
	* Its size allows to reserve large address blocks for specific use and to aggregate addresses for more efficient routing
	* A unique local address (ULA) in IPv6 is reserved for local use and corresponds to fc00::/7
		* It is the equivalent of a private IPv4 address
		* An address in this range can be used without registration in the scope of a private network
* `ifconfig` can be used to configure and inspect the network interface on a Linux system
* The loopback network device: a connection to the same machine
	* It is entirely managed via software by the OS and does not send any packet to network devices
	* It is assigned to the block 127.0.0.0/8 in IPv4
	* In practice it is used almost always only the address 127.0.0.1
	* `localhost` is mapped to 127.0.0.1 in most computers
	* It is used for diagnostic and by applications to reach resources on the same machine (e.g. by Jupyter to show its interface)
* DNS is a hierarchical and decentralised mapping system between IP addresses and mnemonic names 
* A communication protocol is a set of rules for exchanging data over a network
	* In a protocol stack each protocol uses services from the one below it
	* A protocol stack is HTTP running over TCP which runs over IP, which uses a IEEE802 protocol (Ethernet, WiFi)
* IEEE802 is a family of IEEE (Institute of Electrical and Electronic Engeneers) standards dealing with LANs and metropolitan area networks
	* Ethernet (also called LAN) is a family of protocols used in wired LANs, described by a set of standards called IEEE 802.3
	* Wireless LAN (also called WLAN or WiFi) is another protocol standardized by IEEE 802.11 that shares many properties with the wired Ethernet protocol
* Network bandwidth can refer to different concepts
	* The channel bandwith refers to the gross transfer rate of the payload and also of the overhead control information
	* The goodput is the actual rate of payload transfer
* Latency is measured as end-to-end delay (OWD) or round-trip-time (RTT)
	* The OWD is the time that a packet takes to travel from source to destination
	* The RTT is the time that a packet takes to travel from the source to the destination and back to the source
	* The RTT is usually twice the OWD, but not necessarily (upload and download latencies can difffer)
	* The RTT can be assessed with the `ping` command on a Linux system
	* Latency can never be smaller than what the speed of light requires!
* Network adapters are physical devices that connect a computer to a network
	* They can be part of the motherboard or can be plugged in as expansion cards
	* They implement the OSI layers 1 and 2
	* Netwrok adapters are Ethernet adapters, WiFi adapters, Fiber Channel adapters
		* Typical latencies are around 50-125 $\mu$s
		* Ethernet can reach a bandwidth of 10 Gbit/s
	* There are also high-performace adapters used for high-performance computing like Omnipath (Melanox) and Infiniband (Intel)
		* They provide high bandwidth and really low latency network interfaces
		* Typical latencies are less than 5 $\mu$s
		* They can reach a bandwidth of 100 Gbit/s
* A hub is a network device that broadcast the same packet to all the devices connected to it
	* It is used for connecting segments of LAN
* A switch is a network device that statically delivers a packet to a specific machine
	* It knows the MAC of all the devices attached to it and can identify which machine sits at which of its ports
	* It works at OSI layer 2 (and in some cases also at OSI layer 3)
	* It does not increase significantly network response times since it knows to which port each packet should be sent to
* A router is a network device that delivers a packet to an IP address
	* It works at OSI layer 3
	* It can sit between 2 LANs, between a LAN and a WAN, or between a LAN and the network of an ISP
* Top-of-the-rack switching: a switch that delievers packets to a rack of servers and sits on the top of a server rack
	* Usually there are also aggregation switches that deliver packets to the right top-of-the-rack switch
* Some useful network commands (from the `bind-utils` package)
	* `ping`: test connectivity and latency
	* `traceroute` or `tracepath`: check the path to a server and the segment latencies
	* `ifconfig` or `ip addr show`: inspect the configuration of the network devices
	* `ethtool`: for the configuration and diagnosis of network interface controllers
	* `netstat`: statistics on the connections available
	* `host`: get information on a host (form its IP or name)
	* `dig`: lookup a name
	* `whois`: pulls information on an address from IANA (Internet Assigned Numbers Authority)

## Computing Infrastructures
* A computing farm is a collection of servers and it can have millions of cores
	* Network devices manage communication among servers and the interactions with users
	* The Intel Xeon CPU is often used in datacenters since it is reliable and can work continuously
	* The link between sockets in the same motherboard is called qlink
	* Servers are organised in hot islands which are separated by a cooling system
* In a datacenter typically multiple users share the same resources
	* It is important to organize resource usage so to avoid wasting computing power
	* Different users could have paid for different a Quality of Service (QoS)
	* Different users can have different priorities
* A batch system (or scheduler) manages the concurrent access to resources, respecting priorities and usage shares as much as possible
	* It is an application that controls the inattended (batch) execution of jobs (task to be executed)
	* There are many batch schedulers: HTCondor, OpenLava, LSF, ...
	* A batch system takes care of scheduling non-interactive jobs and manages resource access
	* It provides a single point of control for jobs submitted to the CPU farm
	* It dynamically allocates jobs so to maximise cluster use, minimise latency and respect fairshare on a time window
		* A computing farm is usually shared among paying customers
	* Jobs are often organised in queues
* A single job is batch instruction that occupies a single slot and it is executed in a single core
* A DAG workfolow is a series of jobs dependent from each other described by a directed acyclic graph
	* It is essentially a pipeline
	* The output of a job is the input of another
* A collection is a group of jobs that can be run in parallel
	* They typically act on different input data
* A parallel job is a job that needs to run in more than 1 core
* A parametric job is a collection that can be easily defined by a parameter
* Fair share scheduling: each user should obtain its fair share of resources, depending on the QoS he paid for
	* Normally jobs are dispatched with a FIFO behaviour (first come first served, FCFS)
	* With fair share scheduling, the load is redistributed across queues so that no queue becomes starved and no user can monopolise resources
	* Fair share does not mean necessarily equal share, customers could have paid for different QoS levels!
* Reservation: the batch scheduler can reserve cores for 1 job that is waiting for something to be executed
	* This is typical of parallel jobs that are waiting for enough cores to be available
* Backfill: while the reserved cores are idle they can be used by other jobs whose duration does not exceed the starting time of the job that reserved the cores
	* Only jobs that will finish before the job that reserved the cores will start are permitted
	* For backfill to be possible, the user must declare the duration of his jobs!
	* After the pre-determined time expires, the job is killed by the scheduler
* Main messagges
	* Concurrency in a datacenter is handled by a batch system
	* Jobs are typically unattended
	* Fairshare uses a dynamic priority to ensure the respect of the agreed usage quotas
	* Dynamic priorities depend on a large number of factors
	* The batch scheduler minimizes the waiting time for customers and maximizes cluster utilization
* Jobs are composed of
	* Job type
	* Prologue: initial checks to be performed
	* Input sandbox: the list of needed files for the job
	* Requirements: the hardware required for the job
	* Executable: the actual application to run
	* Where the stdout and stderr of the application should be directed
	* Output sandbox: the files that will be produced by the application
	* Epilogue: final cleanup, file uploads, updates, ...
	* Error recovery: what to do if the job fails

## Storage
* Storage devices are Hard Disks (HDDs), Solide State Disks (SSDs), tape, Non-Volatile Memory (NVM)
* The performance of a storage device is described in terms of storage capacity, bandwith and Input/Output Operations Per Second (IOPS)
	* The bandwith is the read and write speed for sequential data on the drive
	* The IOPS is the number of I/O operations per second that can be requested
		* It is important when operating on small files
* An SSDs use NAND technology, it is much slower than RAM but non-volatile
	* It can withstand a limited number of write cycles
	* NAND SSDs use NAND logical gates
	* The NAND used in USB drives tend to be less performant, cheaper and less durable than the one used in SSDs
	* Bandwidth is of 400/500 MB/s, 100k/400k IOPS, capacity of 500 Gb
	* The biggest advantage of an SSD is in terms of IOP
* Hard disks are slow since they have mechanical moving parts
	* They have spinning disks and a moving head
	* Speed is 100/150 Mb, 100/200 IOPS, capacity 8 Tb
* Tape storage is expensive since it requires a special infrastructure (a tape library) but it is really scalable
	* Speed is 250 MB/s, sequential access (no IOPS definable), capacity 8.5 Tb
* Data maintainance is a huge responsibility, since it could be impossible to re-obtain lost data
* RAID (Redundant Array of Independent Disks) systems allow to virtualize data storage devices
	* The purpose of a RAID system is to increase data redundancy, imporve performances, or both
	* The RAID level can be considered as a type of QoS
* RAID0: file stripping at the block level
	* A single file is stripped into several drives
	* I aggregate $n$ physical disks into 1 virtual disk
	* I get higher performances but no redundancy
	* Losing only 1 disk means losing all the data: there is no redundancy
	* The transfer rate is up to $n$ times higher than whoat it would be on a single disk
		* The transfer rate is maximal when the file to read or write is equally divided among the disks
	* The total virtual storage size is $n$ times the size of the smallest disk
* RAID1: file mirroring
	* Performances can imporove for reading operations, while they remain at the level of single disks for writing
		* I can access different locations of the same file at the same time from different disks
	* An example is 2 disk that operate as 1, mirroring their contents
	* The redundancy level is always $n-1$
	* The storage space is equal to the capacity of the smallest disk
* RAID2 is rarely used and involves stripping at the bit level
	* It uses an Hamming code for error correction
* RAID3 is rarely used and involces stripping at the byte level with a parity disk
	* A parity disk contains parity bits for each block, that are used in error correction
	* It requires the rotation of all the disks to be in sync!
* RAID4: block-level stripping with parity disk
	* It is similar to RAID0 but it also has a parity disk
* RAID5: block-level stripping with distributed parity
	* It is similar to RAID0 but it uses parity blocks, distributed among all the disks
	* It requires at least 3 disks, since a full disk capacity is used for the parity blocks (but distributed across all the disks!)
	* It is more reliable of RAID0 because of parity, but also less performant
	* It is tolerant to the loss of an entire disk from the array
		* Its data can be reconstructed from the parity blocks
* RAID6: block-level stripping with double distributed parity
	* It is similar to RAID5 but it uses 2 parity blocks instead of 1
	* It requires a minimum of 4 disks
	* It can tolarete the concomitant failure of 2 disks
* A file system controls how data is stored and retrieved
	* It manages the space on the drive, keeping track of which physical locations contain which files
	* It uses filenames as a reference to specific physical locations
	* It uses directories to group files into separate collections
	* The allocation of space on a drive can be implemented with an index table, or with an inode (index node, typical of Unix-like systems)
	* It can or not suppor file metadata like owner, permissions, access times, dimension of the file, creation time, edit time
* The POSIX (Portable Operating System Interface) is a family of standards defined by IEEE for maintaining compatibility between operating systems
	* POSIX defines the API, as well as command line shells and utility interfaces
	* POSIX is defined in the standard IEEE 1003 and in ISO/IEC 9945
	* It also define the characteristics of a POSIX file system
	* Most Linux file systems are POSIX-compliant (ext3, ext4, zfs, xfs)
	* A POSIX filesystem basically is a file system that supports file-open operations
* A Direct Access Storage (DAS) system is a digital storage device directly attached to the computer accessing it
	* It does not incorporate any network capability, but it can be exposed to a network by the computer accessing it
	* A DAS is connected to an host trough a Host Bus Adapter (HBA)
	* Cables are important, especially for DAS systems
		* The main protocols used are ATA, SATA, NVMe, SCSI, SAS, USB, and fiber channel
* A JBOD (Just a Bunch Of Disks) is a container containing disks that can be plugged into a server
* A NAS (Network Access Storage) is a file-level storage server exposed to a network
	* It provides file level access for external clients
	* It is usually represented by a purpose-built computer that hosts a collection of storage devices, often in a redundat or RAID arrangement
	* It uses file sharing protocols like NFS and SAMBA
	* A NAS removes the file-sharing responsibility from other computers on the network
* A storage area network (SAN) is a dedicated network that provides storage access at the block level
	* With a SAN I am not exposing the file system, but the disk itself
	* The connections are made by Fibre Channel, iSCSI, or Infiniband
	* A SAN is composed of a series of storage and network devices, that can be dedicated or not
	* A file system can be created on top of a SAN to provide file-level access
* A SAN is composed of an host layer, a fabric layer and a storage layer
	* The host layer is composed of servers that allow access to the SAN and storage devices
		* The communication between the host layer and the storage devices happens trough HBAs (usually cables)
			* A GigaBit Interface Converter (GBIC) is used to convert ligth to digital signals
	* The fabric layer is composed of the SAN networking devices
		* It includes cables, routers, gateways, switches
		* Network devices move data within the SAN and between an initiator (HBA port of a server) and a target (the port of a storage device)
		* SAN networks are typically redundant, so SAN switches tend to be connected by redundant links
	* The storage layer is composed of the storage devices
		* HDDs are usually connected in JBODs and organised in RAID systems
		* Tape devices are arranged in libraries
		* Every partition of every storage device is identified by a logic unit number (LUN) in the SAN
		* The LUN allows to restrict access to data in the SAN and to segment the storage space
* Important data need to be backed up frequently and possibly moved to a different geographical location
* A parallel filesystem is a single filesystem across multiple networked servers
	* It facilitates high-performance access thanks to the use of coordinated I/O operations between clients and storage nodes
	* It usually supports a high mutliplicity of clients (thousands of them!)
	* It is built on a SAN, with block level access
	* Files are striped across multiple local and remote storage devices
	* The user of a parallel file system is not required to know the block location of files to access them
	* The system uses a global namespace
	* It maintains metadata servers with information about the location of the blocks for each file and their metadata
	* Metadata in a parallel file system are essential and cannot be lost: metadata servers have a lot of redundancy
	* Capacity and bandwidth can be scaled depending on the requirements
	* Parallel file systems are typical of high performance computing environments
	* They are designed for performance and highly concurrent access
	* Examples of parallel file systems are LUSTRE and IBM Spectrum Scale (General Parallel File System, GPFS)
* A distibuted file system is built on a system with file-level access
	* It does not provide block-level access to clients
	* It creates a unique global namespace for distributed file
	* Files on a distributed file system can be accessed with the same semantics used for local files
	* A distributed file system is built on top of the file systems of the disks on the various servers!
	* They are typically slower than parallel file systems
	* Examples of distributed file systems are HDFS, BeeGFS, GFS, ...
* Note: the distinction among parallel and distributed file systems is not binary, and some file systems present characteristics of both
* The tape area network (TAN) is a subsection of a SAN dedicated to tape devices
	* It is composed of the interconnections among servers, libraries and tape devices
	* Tapes are organized in libraries containing tape drives and robotic arms that move the tape cartridges into the drives
	* A tape library can have a 85 Pb capacity and frequently has a disk buffer for performing read and write operations on tapes
	* At CNAF 80 Pb of tape storage are used for RAW scientific data and for backing up server configurations, logs, and repositories
* Tiered storage is a data storage environment organised in tiers according to the QoS of its different storage devices
	* Tiers differ for storage price, performance, capacity, and/or function
	* Tier 1 storage is used for hot data (frequently used data)
		* It is composed of large RAID systems and SSDs 
	* Tier 2 is used for warm data
		* It is mainly old disks and small RAIDs
	* Tier 3 is used for cold data like backups and rarely accessed data
		* It is mainly tape storage
* Moving a file to an higher QoS tier is called a recall, while moving it to a lower tier is called a migration
* A storage device that declares a certain QoS ensures that a particular application always can benefit of a certain minimum performance level
	* For storage devices, QoS is often expressed in terms of IOPS
	* Nowadays many storage systems claim to offer some form of QoS
* IBM Spectrum Protect (formerly TSM, Tivoli Storage Manager) is proprietary software from IBM which is leader in data protection solutions
	* It is used mostly for backup and archive purposes
	* It offers a Hierarchical Storage Management (HSM) extension to manage migrations and recalls between disk and tape storage of data hosted on a Spectrum Scale file system
	* The mean daily transfer rate for each server is of 600-650 Mb/s
* Tape is becoming popular again since the amount of data to be stored increases exponentially while HDD capacity has stagnated
	* 80% of the newly created data is cold data, which is not accessed in at least 3 months: it is ideal for tape storage
	* Tape storage is energy efficient: no power needed when not in use
	* Tape storage is extremely safe: I can put the cartridge in a safe box and it is inaccesible for everyone
	* Tape devices are expected to last for more than 30 years and are very reliable
		* Data can often be recovered also in case of drive failure
		* The data is verified by a read-while-write system
	* Tape storage is extremely safe: I can put the cartridge in a safe box and it is inaccesible for everyone
	* The main advantage: tape is really cheap
* A Storage Remote Access Service is a service that grants remote access to file system
	* It implements operations like list, copy, delete, migrate, recall
	* It should be possibly based on a standard or de-facto standard
	* It provides various types of auth/authZ mechanisms such as username and password, tokens, and digital certificates
* Data transfer applications can implement asynchronous data movement or data streaming
	* Asynchronous data movement applications are `scp`, `rsync`, `ftp`
	* Streaming applications are Flume and Kafka
* GridFTP is an extension of the File Transfer Protocol (FTP) used for distrubuted computing
	* Provides a reliable and high-performance transfer of large files
	* It is extensively used at LHC
	* It can use multiple concurrent TCP streams
	* It allows the transmission of partial files
* Main messages
	* DAS is a devicde directly connected to a server
	* NAS provides file level access to storage devices through a network
	* SAN is a dedicated network infrastructure that provides access at the block level
	* Parallel and distributed file system manage highly concurrent access to data over multiple servers
	* A datacenter can provide storage resources with different QoS

## Data center management for Big Data
* HyperConverged architecture: use of general-purpose low-cost hardware instead of dedicated systems
	* It is becoming increasingly popular
	* Storage and computing happen on the same consumer-level machines, not on separate and dedicated areas of a server farm
	* It is suitable for Big Data and MapReduce applications
	* It is easily scalable
* Provisioning: the deployment of thousands of servers in a datacenter can be facilitated by automated tools for installation and configuration
	* Foreman is an application that manages the lifecycle of servers (physical or virtual)
		* It is open source, accessible from a web interface, an API, or the command line
		* It allows to define the OS to be installed, the installation medium, files to be executed
		* If integrated with Puppet it acts as an external node classifier
	* Puppet is an application for the automatic deployment and configuration of servers
		* It is open source and works through modules written in a declarative language (many contributed modules are available)
		* It is composed of a Puppet master and a Puppet agent
		* The Puppet master knows how the nodes should be configured and compares their actual configuration with the desired one
		* The Puppet agent sends to the master the actual configuration of nodes and executes the proper actions to apply the desired configuration
* Monitoring and alarming: monitor the operations of the datacenter and report anomalies
	* Monitoring data is typically accessed from a web interface or with a reporting tool
	* An alarming system notifies administrators in case of anomalies
		* An anomaly can be a server crash, or the passing of a threshold (disk usage, memory, CPU)
		* It can hanlde specific events, for instance restart a service in case of a crash
* The fast-performing interconnections of a motherboard form the northbridge, which connects CPU, memory, and PCIe devices
* The slow-performing interconnections of a motherboard form the southbridge, which connects the northbridge with PCI, USB, SATA, IDE, BIOS, and legacy devices

## Power and cooling
* The power infrastructure of a datacenter provides electricity to all the components of the farm
* It can emply Uninterruptable Power Supplyes (UPSs), a system that prevents failure in case of electrical cuts
	* It can be based on batteries, inertial systems, engines, or some combination of these elements
* The cooling system of a datacenter can include free cooling, forced air flow, liquid submersion, liquid cooling, heat pipes, and many other systems
	* Liquid submersion uses non-electrically conductive liquids such as oils
* The Power Usage Effectiveness (PUE) of a datacenter is the ratio among the energy used for computing and the energy used for overheads like cooling
	* Its ideal value is 1.0: all the energy is used for IT systems and not for overheads
	* The PUE is the inverse of the DataCenter Infrastructure Efficiency (DCIE)
	* In 2008 Google had a PUE of 1.21 across 6 of its centers

# Hadoop and MapReduce
* To work with Big Data, you need an infrastructure which is capable of working with a huge volume of unstructured or semistructured data in real time
	* Typically this infrastructure is the cloud
* There are 2 main ways of dealing with Big Data
	* Storing data on non-relational databases like MongoDB (a NoSQL database): this requires little coding skills
	* Storing data on massively parallel database systems and using MapReduce applications: typically requires a specialised data scientist
* The Big Data software ecosystem is too damn big
* The Hadoop ecosystem is a open-source system for dealing with Big Data
	* It uses the HaDoop File System (HDFS) for storage
	* It uses YARN for resource management
	* It takes advantage of the MapReduce paradigm
* MapReduce is an algorithm developped by Google for parallel and decentralized processing and generation of big data
	* It does not rely on a centralised database and it usually uses a distributed filesystem like HDFS
	* It is based on the Map and Reduce actions
		* Map: convert a set of data into another, described by key/value tuples
			* I can take a document and form a dictionary with single words as keys and their count in the document as value
		* Reduce: aggregate the data from a set of tuples
			* I take several dictionaries from different documents and count the total word occurrence
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


## Hadoop

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
