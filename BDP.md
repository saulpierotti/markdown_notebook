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
	* It offers CPU and storage resources to many INFN initiatives
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
* MapReduce is an algorithm developped by Google for parallel and decentralized processing and generation of big data
	* It does not rely on a centralised database and it usually uses a distributed filesystem like HDFS
	* It is based on the Map and Reduce actions
		* Map: convert a set of data into another, described by key/value tuples
			* I can take a document and form a dictionary with single words as keys and their count in the document as value
		* Reduce: aggregate the data from a set of tuples
			* I take several dictionaries from different documents and count the total word occurrence
* Apache Hadoop is an open-source software ecosystem for big data analysis and storage
	* It is designed to scale well from a single server to thousands of servers
	* It is highly fault tolerant
	* It is typically run on low-grade hardware, but it is highly reliable because of the software-level failure handling routines
	* New nodes can be added quickly without changing configurations
	* It does not require any schema, it can accept any kind of data
	* When a node fails the system just redirects the load on the remaining nodes, without halting
* Hadoop is composed of
	* Hadoop Common: a series of common utilities that support the other modules
	* Hadoop Distributed File System (HDFS)
	* Hadoop YARN: framework for job scheduling and resource management
	* Hadoop MapReduce: a YARN-based system for parallel processing based on the MapReduce approach
	* Hadoop Ozone: an object storage service
	* Hadoop Submarine: a machine learning engine
* The Hadoop Distributed File System (HDFS) is the core component of the Hadoop ecosystem
	* It creates a level of abstraction above the resources
	* It allows to see the whole HDFS as a single unit
	* It stores data in the various nodes and mantains a log of the stored data
	* It is composed of 2 core components: NameNode and DataNode
	* The NameNode is the metadata server
		* It does not store the actual data
		* It has high computational requirements but low storage requirements
	* The DataNodes actually store the data
		* They can be represented by commodity hardware
		* They tend to be storage-specialised systems
	* There is typically only 1 NameNode and many DataNode in an Hadoop cluster
* Writing in an Hadoop cluster requires 2 essential pieces of information to be submitted with the data: block size and replication (number of copies of the block that I want to be stored in the Hadoop cluster)
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
	* The DataNodes every 3 seconds send a HEARTBEAT message to the NameNode, signaling their presence
	* If the NameNode does not receive the HEARTBEAT from a DataNode in 10 minutes (because it is dead or there is a network failure) it considers it dead
* Network failure handling in Hadoop
	* Whenever data is sent the receiver returns an ACK (acknowledge) message
	* If the ACK message is not received after several trials the sender assumes the receiver to be dead
* Corrupted data in Hadoop
	* Data always include a checksum when it is sent and when it is stored
	* DataNodes periodically send a BLOCKREPORT to the NameNode, a list of all the blocks in the node
		* Before sending the BLOCKREPORT a DataNode checks all the block checksums
		* If a block is corrupted it is not sent to the NameNode
		* The blocks that the NameNode knows to be stored in a specific DataNode but that are not included in the BLOCKREPORT of that DataNode are assumed to be corrupted
* The NameNode always mantains 2 essential tables: a list of blocks and a list of DataNodes
* When a DataNode is dead or assumed dead, it is skept for all transactions both by client and NameNode
	* If it is so the data will not reach the desired replication, but the NameNode will subsequently instruct the DataNodes to copy data from each other accordingly
* In order to be as resilient as possible, block replicas are kept at most as 1 per server and 2 per server rack, if possible
	* It is also possible to specify a custom placemnt algorithm
* YARN allocates resources and schedules jobs in the Hadoop cluster
	* It is composed of 2 major components: ResourceManager and NodeManager
	* The ResourceManager is the central node of the cluster
		* It receives requests and dispatches them to the relevant NodeManagers
	* The NodeManagers are installed onto each DataNode and manages task execution of that node
	* ApplicationManagers accept job submission and forwards them to the respective ApplicationMaster on the DataNode
* Hadoop MapReduce is the core processing component of the ecosystem
	* It is a software framework for writing applications that process large datasets using distributed and parallel algorithms in an Hadoop environment
* SQL is a relational DBMS based on tables
	* It works with a specific schema
	* It uses the powerfull SQL query language
	* Implementations are MySQL, Oracle, Sqlite, Postgres
	* It is typically commercially supported
	* It focuses mostly on consistency: typical application is the database of a bank
		* We can say that it focuses on the ACID properties: atomicity, consistency, isolation, durability
	* Scalability is vertical
* NoSQL is a non-relational and document-based DBMS
	* It can consist in key-value pairs, graphs, wide-columns
	* The schema is flexible and it can also host unstructured data
	* Scalability is horizontal: I can just increase the number of servers in the pool
	* It uses the non-standard UnQL query language (unstructured query)
	* Implementations are MongoDB, Cassandra
	* It is typically supported by the community
	* It focuses on availability: it does everything possible to remain operational also in case of errors
	* Consistency is eventual: it is not guaranteed at the end of each transaction but eventually it is restored when there is time available for the operation
	* Apache Cassandra is open-source and distributed
		* There is no central node, so no single point of failure
		* It works with wide-columns
		* It was initially developped at Facebook
		* It supports the Hadoop integration and MapReduce
		* It uses the novel query language CQL
	* Apache Kafka is a distributed streaming platform

# Virtualization
* Virtualizing means creating a virtual version of a physical resource through an abstraction layer that hides the underlying implementation
* Virtual machine are hardware-independent and their resource usage can be dynamically adapted
* Virtualization advantages
	* Thanks to virtualization I can consolidate the services provided by many servers into a single machine
	* Applications are sandboxed in a virtual environment
		* I can test code and applications without risking to crash the whole physical server
		* I can create a dedicated envronment for legacy applications
	* Virtual applications can be provisioned on demand
	* Hardware and software are decoupled: I can move VMs betwenn different hosts and I can suspend a VM when not needed
	* I can emulate hardware which is not present on the physical host
	* I can run applications that are not compatible with the OS of the physical machine
* Virtualization disadvantages
	* Virtualization is vulberable to bugs and hacking, since many different hosts and OSs are co-existing on the same hardware
		* VM-to-VM attack: a VM can have unauthorized acces to data of another VM
		* VM-to-HV attack: some hypervisors (KVM or XEN) work directly at the level of the hardware: everything can be compromised
	* Performances in a virtual environment can be worse due to the overhead for the physical host
		* This is true particularly for I/O operations
* Provisioning of VMs is NOT cloud computing if it does not respect the self-service, on-demand, network-based, elastic offer and pay-per-use paradigms (see next section)
* KVM is a Linux kernel module for virtualization

# Cloud Computing
* Cloud computing deals with supplying information and communication technologies as a service
* The cloud model is focused on the concept of offering a service, without the need of thinking about the underlying physical infrastructure
* It enables uniquitous access to shared pools of configurable system resources and higer level services that can be rapidly provisioned with minimal management effort, often over the internet (definition from the US National Insttitute of standards and technologies, NINST)
* It is similar to a public utility in that achieves economy of scale and coherence: the cloud is a utility service
* Cloud essential characteristics
	* Self-service, on-demand: computing capabilities can be provisioned unilaterally from the client, without the need for human intervention
	* Netwrok-based access: capabilities are available over the network and accessed trough clients
	* Resource pooling: physical resources are pooled by the cloud provider and the user has no control or knowledge of them
	* Elasticity: resources can be easily scaled up or down in response to demand, with minimal delay and apparent infinite capacity
	* Pay-per-use: the customer doen not incur in any upfront cost
* Cloud computing is not the same as virtualization but it can employ virtualization to pool physical resources
* A cloud infrastructure has a teorethical infinite capacity, but you need infinite money to use it!
* Infrastructure as a service (IaaS): the customer receives a machine with an OS
	* It can provide storage, computational and network services and it is often virtualized
* Platform as a service (PaaS): the customer manages data and software, but no direct access to the OS
	* I can ask for a HTC-Condor cluster already functional, a parallel file system, an SQL database
* Software as a service (SaaS): pre-formed environment entirely managed by the vendor
	* Gmail infrastrucutre for managing the email of a company
* At the end, what matters for the user is the application: don't focus so much on the implementation!
* The cloud paradigm has 3 main dimensions: service model (Iaas, PaaS, SaaS), deployment and isolation
* The service model is what said before: IaaS, PaaS, SaaS
* Deployment refers to where the services are distributed and it can be public, hybrid or private
	* A private cloud is accessible only to insiders and it rarely has infinite resources
	* A community cloud is available to a community of organizations sharing a common goal
	* A public cloud is AWS or Google Cloud, which can be assumed as infinite
	* An hybrid system is a combination of the above
		* I can use a private cloud system that redirects peak requests to a public system
		* I could also decide to use a private system for sensitive data and a public cloud for non-sensitive data
* Isolation concerns how I isolate the servies offered to different customers
	* A dedicated cloud is dedicated to a scope (es. Bioinformatics)
	* A multi-tenant cloud is multi-purpose and is used by customers with different goals
	* I can also consider a tenant as a group of customers (es. research group), that payed for a specifc QoS
	* The isolation type is essential for determining how to deal with resource segmentation, data protection, application security, auditing, and disaster recovery
* The main clud use-cases are
	* End-user that interacts directly with the cloud
		* It should be easy to access without any specific technology (it should be an open client)
		* If need by the application, it should provide means for secure authentication
		* It should focus on privacy and security
		* The Service Level Agreement (SLA) tend to be simple
	* Enterprise that uses the cloud to provide services to a end user
		* SLA tend to be detailed
		* It should provide, if needed, means of authentication for customers of the enterprise
		* It should be location-aware for legal purposes
		* It should proved monitoring services for the enterprise
		* It should provide standard APIs for different vendors
	* Enterprise that internally uses cloud services
		* It may function as a suppletive storage
		* It may provide peak resources
		* It should use standards to avoid vendor lock-in (from the perspective of the enterprise)
	* Different enterprises that use the same cloud
		* It must handle correctly concurrent access
		* If some resources (es. storage) are shared, they must be reliably modified by both enterprises
	* The implementation of a private cloud
		* It does not require standard APIs, concurrency management, and other issues typical of a public cloud
	* The process of changing cloud provider
		* Here standardization is essential
	* The creation of an hybrid cloud
		* For the end user the shift from the private to the public cloud should be transparent
* Migrating an application to the cloud can be motivated by reduction of costs, business agility and savings on management
	* Public clouds can be adapted much quicker to the demand!
* The choice of a public or private cloud can be influenced by the cost of WAN traffic, security concerns and integration with pre-existing applications
* Migrating to a SaaS is not actually a migration but a change of application
* Web hosting is one of the most common cloud use cases
* Cloud computing services can be provised with or without virtualization
	* Cloud virtualization often allows to reduce operational costs
	* In many cases containers can be provided instead of full-blown virtual machines
	* A VM is only a building block: real life apps need databases, autoscaling features, ecc.
	* The Cloud is much more than provisioning VMs
* Multi-tiered application are organized into a data management tier, a business logic tier and a presentation tier
	* The data management tier concerns with the databases
	* If well designed it is possible to migrate the tiers independently to the cloud
		* This is not always possible, for example in cases with high network traffic between tiers
* A stateless service does not store the state (a non-interactive web server is stateless)
* A stateful service stores information about user interactions (a shopping cart is a stateful application)
	* It cannot be replicated easily!
* A cloud-aware application is stateless and distributed
	* Disaster recovery and scaling should be built-in in the app, not rely on system features
	* If there is a rise in requests I can just duplicate the system and create a new instance
	* Cloud-friendly applications are like cattle: I can easily replace them when needed
* Legacy applications are stateful and monolitic
	* Fail-over is managed by the infrastructure
	* Scaling is managed by the infrastructure
	* Legacy applications are like pets: I cannot replicate them and I need to take care of them
* The reduction of costs in the cloud is due to economy of scale and less requirements for management
	* Cooling systems are cheaper if used for huge datacenters
	* Lower hardware and power costs due to more contractual power
	* Management costs are shared for a higher number of paying customers
	* Resource aggregation allows for more efficient utilization
* The cloud democratizes resource access to small actors, since it make the resources more finely subdivideable
* Thanks to its practically infinite capacity, the cloud moves problems from batch mode to real-time mode
* SaaS applications provide ubiquitous access to resources from any device without specific software needed
	* An example is Google Docs, Dropbox
* The rise of cloud computing generates new business opportunities
	* Training and support the use of cloud services
	* Possibility for companies to develop open-source software for the cloud
* Cloud risks: security, privacy, vendor lock-in, data loss, isolation failure, incomplete data deletion
	* In the terms of service for standard accounts there is no guarantee of continuity, reliability, ecc
	* In many case cloud services are not completely mature
* AWS was launched in 2006 and it had a revenue of 17.5 billion dollars in 2017
	* It provides services to governments, companies, and individuals on a paid subscription basis
	* Most of its revenue is from IaaS
* Cloud provisioning Terms of Contract (ToC) explicitally decline any responsibility for unavailability or loss of data
	* There is no guarantee that the service will be uninterrupted, error-free, or free from harmful components
	* There is no guarantee that the data are stored safely and without any risk of data loss
	* The service is provisioned "as is"
	* The user is responsible for keeping its data safe, secure, and for making backups
* The set of cloud technologies is sometimes not completely stable
	* Tuning and experts are often needed
	* Sometimes non production-ready solutions are offered in order to avoid complex configs
* The cloud raises serious privacy and security concerns
	* How do I know that when I terminate a contract with a provider my data is actually deleted?
	* How can I avoid vendor lock-in
* Is my data on tyhe cloud safe from governments?
	* The CLarifying the Overseas Use of Data (CLOUD) Act, signed in the US in 2018, allows US officials to turn over user data regardless of the physical location of the servers
	* UK law requires ISPs to store the browsing history of clients for one year
* It is really hard to delete someone's own account from certain websites
	* `justdelete.me` provides a list of website categorized on how hard is it to delete an account hosted on them
		* It also provides instructions for how to do it
	* For some websites, it is actually impossible to delete an account: Wikipedia, Steam, Starbucks, Netflix, Evernote, Wordpress, Udacity, Pastebin
* The EU and the US have a very different privacy approach
	* Regulations in the EU are more stable across legislations
	* In EU individuals have more control over their data
	* The same authority enforces privacy laws in the EU, while several governmental organization do so in the US
	* There are fewer organizations that support privacy in EU
	* EU citizens, but not US citizens, have the right to be forgotten
* The General Data Protection Regulation (GDPR, 2018) is a EU regulation that enforces privacy of personal data
	* The fines for breaching GDPR are of 20 million € (or 4% of global turnover, whicherver is greater)
	* Personal data is any information related to a natural person or Data Subject that can be used to identify (directly or indirectly) the person
		* It can be anything, from an IP address to a picture to an email address
	* For non-personal data (e.g scientific data non related to Data Subjects) it is required
		* Free movent of data within the EU (no strict data localization)
		* Data availability for the authorities of the EU
		* Free porting of data (no vendor lock-in)
* Some common cloud misunderstandings
	* Capacity is theoretically infinite, but it is not infinite in practice (as well as credit card limits are not infinite)
		* We may not be able to obtain the QoS that we need, when we need it
		* We may be asked a hefty price for what we need
	* It is not easy to decide if a public or private cloud is best for our needs
		* I should evaluate the risk for data loss and leakeage, and the terms of the ToC
* In 2021 28% of total market revenue for infrastructures, middleware and applications is expected to shift to the cloud
* In 2021 70% of public cloud service revenue is dominated by the top 10 providers
* There is no cloud, it's just someone else's computer

# Computing models
* Workload management is the process of determining the proper workload distribution so to provide optimal performances
	* It controls where each job is run in order to maximise workload throughput andn ensure that each node is not over/underused
	* It handles job status, monitoring, information retrieving, and eventual input/output sandboxes
* Job scheduling in distributed infrastructures is challenging
	* Eager scheduling (push model) binds a job to an available resource as soon as possible, and executes it on that resource
	* Lazy scheduling  (pull model) helds the job until a resource becomes available: jobs are extracted from a queue as soon as resources are available
* A Workload Managament System (WMS) can be developped in house for simple workloads, but it is almost always better to use community developped applications
* In a push submission model, jobs can be submitted trough the WMS or directly to computing resources 
	* The WMS has a clear picture of the state of the resources, and so it can distribute load efficiently
	* In a direct submission model the user has to take care of balancing the load across resources
	* It is possible to build a simple WMS on top of a direct submission system
* A pilot job submission model is a way to implement a pull submission system
	* A special job called Pilot is submitted a priori to all the available resources
	* The Pilot does not execute any payload, but it checks the hardware and software environment
	* Real jobs are pulled by the Pilot from a central task queue
	* If no tasks are available in the queue, the Pilot is terminated
	* A pilot submission mode has several advantages
		* The resources are tested by the pilot, and so there is less risk that they are faulty
		* It is easy with it to optimize the usage of resources
		* It can, to an extent, allow to bypass the priorities set by the sysadmin
	* However, it has also disadvantages
		* It destroys any system of a-priori data distribution and pre-placement
		* The central queue is a single point of failure if not implemented correctly
		* The Pilot job introduces some overhead
* Input and Output Sandboxes indicate the set of files that travel with the job when submitted
	* It is IMPORTANT to use SMALL sandboxes to avoid overloading the server handling them
	* Big files should be transferred using the tools provided by the infrastructure
	* A reasonable size for a sandbox is less than 5 Mb
	* If I use data management command instead of sandboxes, the load for the transfer is on the node and not on the server
* A job contains a prologue that prepares the environment for executing the job
	* It can install libraries, transfer data and executables, check software and hardware
* A job also contains an epilogue that runs post-execution scripts
	* It can transfer output data, update databases, compute checksums and perform final checks
* In some infrastructures the job itself cannot be modified by the user, but only prologue and epilogue can be modified
* Different data distribution strategies can be implemented
	* A-priori push: I know already the resources to be used and I distribute the data before launching the jobs
	* Job pull: the job itself pull the needed data
	* No data distribution possible: the data is already distributed by someone else because of a policy
	* Output data can be left where it was produced, or moved somewhere else (in the job itself or in the prologue)
* When distributing data it is important to consider
	* A backup strategy: using different QoS for redundancy (i.e. tape and HDDs)
	* A failover strategy: use more than one phyisical site
	* Access policies: restrict write access to raw, irreplacable data
	* Dostributing equally the load on the nodes
* Remember: everithing that could go wrong will
* It can be interesting to include input data in the infrastructure itself (VM images or snapshots)
* Also the data management can be delegated to third party services
* Data-driven computing model: I can decide to run my job in the nodes that happen to have the relevant data available
	* Not always I can afford to move data because of policies, privacy, network bandwidth
	* The matchmaking process between jobs and nodes in these cases needs to take into consideration data availability
* CPU-driven computing model: I can decide to send jobs wherever computing power is available, and transfer the data accordingly
	* Data distribution is done a priori or by the job itself
* A real-life complex workflow can be a linear combination of CPU-driven and Data-driven models
	* This is usually the case when different jobs of the workflow need very different hardware architectures (HTC vs HPC)
* The distributed infrastructures we saw until now are localised in the same WAN

# High Performance Computing (HPC)
* High performance computing (HPC): I want to speed up the execution time of single jobs
* GFLOPs: billions of floating point operations per second
	* The max GFLOP of a system can be calculated from the number of sockets, cores per socket, clock frequency and FLOPs per cycle
* TDP: thermal design power, it is the maximum amount of heat that the cooling system must be able to dissipate in typical operations
* The first machines for HPC were vector machines
	* They are contrapposed to the currently used scalar machines for the fact that they could operate directly on vectors with their instruction set
	* They were using single powerfull processors (small for now!)
* CRAY-1 (1976) was one of the first vector machines
	* It was able of 80 MFLOPs in scalar operations and 160/250 MFLOPs in vecotr operations
	* It was consuming 115 kW for operation + 330 kW for refrigeration!
	* It costed 8.8 million dollars
* CRAY-XMP (1982 and 1984) had first 2 and then 4 processors and was capable of 2*200 MFLOPs (800 MFLOPs with 4 processors)
* CRAY-2 (1985) had 4 processor and was able of 1.9 GFLOPs
* Subsequently in the 80s there was a shift for vector machines to massively parallel processors (MPP)
	* They used many standard processors connected in the same machine
	* This shift was made possible by the rise of microprocessors
* The Caltech Cosmic Cube used 64 Intel 8086 processors forming a 6-dimensional hypercube
* A MPP can be a single computer with many networked processors
	* There can be thousands of processors
* In MPP processors need to communicate, since they are operating together on a single job
	*  Low-latency connections between single cores and specialized networks are needed
* In time many dedicated MPP supercomputers were produced
* In 1985 Thinking Machines produced the CM-1, and then the CM-200 and CM-5
	* CM-200 had 65536 1-bit CPUs and was capable of 40 GFLOPs
* Intel Paragon was lauched in 1993 and had 4000 Intel i860 RISC microprocessors
	* It was capable of 184 GFLOPs
* ASCI Red MPP (1997) was capable of 1.4 TFLOPs and it was the first supercomputer above 1 TFLOP
* IBM BlueGene was designed as multiple SoCs (System on a Chips) and was able of 20 PFLOPs
	* It was focused on low power consumption
* A cluster is a parallel computer system made of an integrated collection of independent nodes (each of them capable of autonomous operation) and DERIVED FROM PRODUCTS DEVELOPPED FOR OTHER STAND-ALONE PURPOSES
* It is possible to use a cluster of commercial-grade servers for HPC
	* In this case I need a really low-latency network to make them cooperate effectively
* The top supercomputers in the world
	* The Summit OLCF-4 supercomputer is in the USand it is used for civilian scientific applications
	* Its twin Sierra is also in the US and it is used for nulcear weapons simulations
	* Sunway TaihuLight is a chinese supercomputer used for oil research, weather forecast and drug discovery
* Some trends for HPC
	* Most supercomputers now are built as clusters, followed by a MPP architecture
	* Most supercomputers use Intel technology for their chips
	* Most HPC systems are built for the industry, not for research
	* Nvidia is the main provider of accelerators for HPC systems
	* Lenovo is the main HPC manufacturer
	* China has the biggest share of current HPC systems
	* Main applications of HPCs are astronomy, molecular dynamics, earth simulations, fluid dynamics, brain simulations, general relativity calculations
* The speedup of an application when it runs in parallel on P processors is the ratio among the running time of the same application on a sequential system and that on the parallel system
	* If the speedup is equal to the number of processors it means that there is no overhead for the parallelism: we are in a perfect linear speedup
* The efficiency of a parallel system is the ratio among the speedup and the number of processors
	* It is 1 in case of perfect linear speedup
* In rare cases the speedup can be superlinear, usually because of memory caching
* Amdahl's law predicts the speedup of a computation by assuming linear speedup
	* It leaves the serial processing part of the job untouched while it divides the parallel computation by the number of nodes
	* The maximum possible speedup is $S= 1/\alpha$ where $\alpha$ is the serial fraction of the computation
		* $S=1 / \alpha$ is the actual statement of Amdahl's law
		* The maximum possible speedup is the time without parallelization divided by the time needed for only the serial part
		* This is because the limit of time needed for the parallel part approaches 0 when the number of cores approaches infinity
* HPC systems can use shared memory (RAM) in order to share information among threads and processes
	* Processes can run in the same or different processors when using shared memory
	* This is an efficient mean for sharing information among processes
	* A shared memory can be accessed simultaneously by different processors
	* Also memory sharing among different threads of the same process is referred to as shared memory
	* In uniform memory access (UMA) all the processors share uniformly the same RAM
	* In non-uniform memory access (NUMA) the memory access time depends on the location of the memory relatively to the processor
	* It is relatively easy to implement a shared memory system
	* Communication between processes is as fast as a concurrent memory access to the same location
	* Typical problems of a shared memory implementation are cache coherence and race conditions
	* When I am using shared memory I need to ensure that also the CPU caches are syncronised!
	* A Race condition is when the output of a parallel program changes by changing the order of execution of its threads, and it is generally a bad thing
* The NUMA API is used for setting shared memory allocation policies
	* `libnuma` can be used for setting up a NUMA environment
* OpenMP is another API used for writing multithreaded applications
	* It shares variables among threads and greatly simplifies parallel programming in C/C++/Fortran
	* Communication happens through the sharing of variables among threads
	* It can cause a Race condition when common variables are unintentianally introduced in the threads
	* I can use synchronization to protect data conflicts, but it is computationally expensive
* Distributed memory refers to a multiprocessor system where each CPU has its own private memory
	* Each CPU can only operate on local data
	* A program in distributed memory implementations is a collection of named processes
	* Each process has a local address space without sharing
	* Communication among threads in mediated by explicit send/receive calls
* MPI is an API used for creating distributed HPC systems
	* Its core is representedby the functions `MPI_Send` and `MPI_Recv`
	* The data to be sent or received is blocked, meaning that the function returns only when the data can be safely used
	* The reduction operation can be used for summarising a set of numbers ot a smaller set of numbers
		* It takes the input from the distributed processes and then places the result only in the root process
* Hardware coprocessors can be used for accelerating the FLOPSof a HPC system
	* Coprocessors are not a new idea: in 1980 the Intel 8087 was one of the first floating point coprocessors
		* The 8087 was the first coprocessor to use the x87 instruction set
		* The x87 adopted the important IEEE754 standard for floating point operations
	* Vector coprocessors in time were absorbed into CPUs and now are a main part of every CPU
	* The GPU is one of the most used coprocessors
		* In the 2006 CUDA was born: it is a parallel computing platform for performing general computation on a Nvidia GPU
		* A GPU is driven by a CPU that manages the code to be executed on GPUs, the memory of the GPU and the movements between CPU and GPU
		* Optimized HPC applications can be bounded by computing or by bandwidth
		* When comparing performances of CPU and GPU, be sure that the applications used for the comparison are optimized for both CPU and GPU and that the algorithm is state of the art!
		* When you see claims of 100x speedup due to GPU, be suspicious!
		* A GPU has a penalty compared to a CPU since it needs to move data across the PCI bus from the CPU to the GPU: this must be considered when making comparisons
	* A modern silicon chip contains integrated components: in the same chip I can have CPU, GPU, chaches, and other devices

# HTC
* High throughput computing (HTC) I want to maximise the number of jobs executed, not speed up the single job
	* Many copies of the same job are run in parallel
	* There is no speedup for the single job
	* It maximises the throughput of the system
* HTC infrastructures deliver high computational power in a long time, while HPC infratructures deliver huge computational power in short bursts
* HTC infrastructures are PC clusters, server clusters, distributed systems and grids
* A Grid is an hardware and software infrastructure that provides dependable, consistent, and inexpensive access to high-end computational capabilities
	* A Grid coordinates resources that are NOT subject to centralised control
	* Uses standard, open and general-purpose interfaces and protocols
	* Delivers non-trivial QoS
* The users of a Grid are virtual organizations
	* A cirtual organization is a set of individuals that share resources under certain rules
	* Sharing of resources is highly controlled and well-defined
	* The owner of the individual resources decides who can access them
* First law of the Grid: 95% of the Grid is agreement on protocols between participating institutions
	* Standards, protocols, and interfaces aim at providing common abstractions of different implementations of similar services
* There is no Grid owner and the network is distributed: I do not know which machine is processing my data
	* My job gets processed somewhere, somehow, after some time
* The Grid is similar to the power grid: "We will probably see the spread of computer utilities, which, like present electric and telephone utilities, will 
* The Grid paradigm: a Grid middelware makes supercomputers, PC clusters, scientific equipment, storage devices, sensors, networks and the internet available to users in forms such as mobile access, desktop workstations, and visualization tools
service individual homes and offices across the country" (Len Kleinrock, 1969) 
* Grids can be of different types
	* Grid services based on supercomputers
	* Grids based on conventional clusters
	* Grids based on clusters of desktop PC voluntarily contributed by users, that share part of their computational power
* The LHC computing Grid is a computer Grid established by CERN for dealing with the large amount of data produced by the Large Hadron Collider (LHC)
	* It has a tiered architecture with Tier 0 being the LHC itself, Tier 1 being formed by 11 national datacenters (INFN-CNAF for Italy), and Tier 2 being formed by about 130 other centers
	* It includes 400k logical CPUs, 122 Pb of disk storage, and 128 Pb of tape storage
* The European Grid Infrastructure (EGI) supports scientific research in different disciplines
* Second law of the Grid: anything that can go wrong, will
	* Grids are really complex, and they often fail
	* "A distributed system is one in which the failure of a computer you didn't even know existed can render your computer unusable" (Leslie Lamport)
	* Expect the unexpected (2008 J. Phys.: Conf. Ser. 119 052030)
		* Services don't respond or return an invalid message
		* Air conditioning or power fails again and again
		* A disk fail and you need to recover from a tape backup, but the tapes have been overwritten
		* A service engineer puts a Coke into a machine
		* Oracle returns you not your data but those of someone else
		* A fishing crawler cuts a trans-Atlantic netwrok cable
		* A tsunami does the same in Asia Pacific
	* Bologna, November 9 2017: a major water pipe breaks near the INFN-CNAF datacenter in the early morining
		* The CNAF center was flooded with 50 cm of water on the outside
		* The water inside the center was only 10 cm thanks to water-tight doors
* Grid security
	* The resources on a Grid are accessible to members of virtual organizations
	* The resource owner decides which virtual organizations are allowed to use the resources
	* The Grid implements a single sign on policy: one access system grants all the resources available
	* The Grid should allow for delegation: it should be possible for a user to endow a program with the ability to access on the user's behalf the resources that the user is authorized to use
	* The X.509 certificate is used for signing into a Grid
		* It contains the Public key of the certificate owner, its identity, information on the Certification Authority (CA), time of validity, serial number, digital signature of the CA
		* A X.509 certificate is basically a public key of the certificate owner signed by a CA, with additional metadata
	* A proxy X.509 certificate is a certificate with limited lifetime that is signed with the private key of the root entity certificate, or with another proxy certificate
		* A proxy certificate allows for delegation of authentication to remote processes
	* The X.509 workflow: a CA signs the root certificate of an entity, which is in turn used to sign proxy certificates
		* The proxy certificates are then used to sign daily by the user
* A Grid job is similar to a job in a cluster: it contains input and output sandboxes, the executable, prologue and epilogue, and other information
* Each job on the Grid is identified by an URL containing the address of the server who accepted it and a job ID
	* The job ID is unique and virtually non-recyclable
	* The ID is a random string, since no serial numbering is possible in a decentralised system
* The HTC paradigm is suited to many applications
	* Embarassing parallel jobs
	* Opportunistic usage
* The crunching factor or speedup in a distributed system is the ratio between the time needed to execute a task on a single machine and on a distributed infrastructure
	* It depends on the number of available resources, the priority of the user, the congestion of the infrastructure
	* It is highly influenced by data transfer times and by errors/resubmissions
	* The speedup is very unstable over time

# Containers
* Virtual machines carry quite a bit of overhead due to the duplication of many OS components
* A container is a virtualization framework that includes only an application and its dependency
	* It enjoys the isolation and resource allocation benefits of a virtual machine without much of the associated overhead
	* Containers share the OS and, where possible, libraries, with the host
* Containers require less resources than virtual machines
	* They start faster and run faster than virtual machines
	* Many more containers than VMs can fit in the same host
* Very important: containers simplify enormously software development and deployment because they allow to encapsulate applications in a controlled and extensible way
* They can be compared to shipping containers for goods
* Docker is one of the most popular container engines
	* It is open source
	* Their website `hub.docker.com` features a git-like repository
	* The Docker engine must be present in the host in order to run a Docker container
	* The Docker engine manages resources for the different containers
	* The same container can be easily shared and run on different hosts (provided that they have the same kernel)
* A (docker) container does not include an OS, it is based on the host OS
	* It operates at the application level
	* It has the same pros without many of the cons of VMs
	* It emulates binaries and libraries needed for the application
	* It is an extended version of `chroot`
* In order to execute a container I just need the right kernel, without worrying about libraries and binaries
	* I also need the docker engine!
* There are many container engines, but they are usually compatible
	* You can build a container with an engine and then run it with another
* Containers are ephimeral: every data in them exists only while the container is running
	* I need to commit the modifications of a container in order to make them persistent
	* Another approach for making data persistent is to bind-mount a host directory to a container, or to create a Docker volume
* Docker can be used for doing development on a local laptop, and then ship it to the production infrastructure
* It is possible to create an application stack with Docker Compose
	* An application stack is a set of containers linked together in order to provide a service
	* Docker Compose is a different software from Docker
	* An application stack can be described with a `.yaml` file, which is parsed by Docker Compose
	* Docker Compose is best suited when autoscaling or a multi-server environment is not needed
	* For more complex setups, Docker Swarm or Kubernetes is preferrable (see BDP2)
* Best practices with containers
	* A container should contain only ONE application
	* The entry point in the container should be explicitly defined (`CMD` field)
	* Keep containers as small as possible
* Some words on security
	* Docker is required for running containers, and it requires root priviledges in order to be installed
	* Containers downloaded from the web may contain viruses
	* Passwords and tokens should NOT be embedded in containers
		* Docker has a purpose-built secret management feature
	* If the host is compromised, container isolation is compromised
	* There can be exploit that allow to breach isolation and interact with the host
	* Since starting containers is easy, it is possible to have a DoS attack
	* Containers should be update regularly when new security patches for the included softwares become available
* Even tough Docker is really useful, many HPC systems and traditional cluster do not have it installed
	* You need root priviledges to install it, or you need to contact an administrator
	* Sometimes administrators do not want to install docker because of security concerns
	* Udocker (INDIGO, INFN-CNAF) is a user-space tool that can run Docker containers without requiring any support from the kernel
		* It is a single python script
	* It is NOT possible to create images from Udocker
		* It does not require root priviledges

# Low power devices
* In the past HPC systems tended to use vector processors, but in time these started to be replaced by cheaper, highly available, and more energy-efficient microprocessors
* Microprocessors started to be mass-produced with the rise of the PC: they are said to be commodity hardware
* System on Chip (SoC) devices tend to have a multitude of different cores
	* There are cores specialised for power efficency, and cores specialised for peak performances
		* This architecture concept is called heterogeneous multiprocessing (HMP)
	* SoCs can be found in mobile devices and embedded systems
* We are now seeing a trend in computing where SoCs are being used more and more, at the expenses of mircroprocessors
	* Is history repeating as for the replacement of vector processors with microprocessors?
	* It is not easy to say, but SoCs are definitively becoming more and more important
* Europe is leader in the production of SoCs and low-power devices
* ARM is the main SoC producer for mobile (CPU and GPU)
	* It was born in the UK, but now it is owned by a japanese firm
* The main producers of SoCs for embedded systems are Siemens, Bosch, Infineon
* The MontBlanc Project is a european energy-efficient HPC project
	* It is based on many ARM SoCs mounted on PCI cards
* Exascale computing with traditional means requires a nuclear reactor for power!
* Exascale computing poses many challanges beside power consuption
	* The cost of the power required
	* The possibility to pack enough components in a reasonable space
	* Resilience to component failure
	* Availability of adequate software for exploiting the architecture
* The general architecture of a HPC low-power system is NOT an iPhone cluster
	* It implements a standard rack confoguration
	* It uses Linux
	* It uses a batch scheduler to handle the execution of scientific jobs
* The ODROID-XU3 board has a maximum power comsumption of 15 W and a cost of 150 euros
	* It uses an ARM big.LITTLE technology with HMP and a Mali-T628 MP6 GPU
	* It uses Ubuntu 14.4 as an operating system
	* It has 2 GB of RAM, an HDMI port and 64 GB of flash storage
* The NVIDIA JETSON TK1 board an ARM+CUDA programmable SoC architecture
	* It is also based on linux
* A System on Module (SoM) is a device that integrates a series on component on a single module (es. a PCI slot)
* When changing the computing paradigm (CPU, GPU, SoC, ...) always ensure the numerical correctness of the results you obtain, do not only look at performances!

# Internet of Things (IoT)
* The IoT is the network of physical devices connected through their electronic components
* Each 'Thing' can be identified via its unique MAC address and is able to cooperate with the existing internet infrastructure
* The IoT is a network of devices that collect and share huge amounts of data
* The collected data are processed in a central Cloud-based service, where it is aggregated with other data and made available to the end-user in a processed form
* IoT increases automation in homes, schools, and businesses

# Fog and Edge Computing
* Traditionally, the wast amount of data produced by IoT systems has been streamed and processed in a centralised cloud
* The access to data through the cloud can be slow because of the time required for streaming data back and forth from the local device
* There can be privacy concerns in streaming certain kinds of data to the cloud
* Case study: self-driving cars
	* The many sensor in a self-driving car produce 40 TB of data every 8 hours of drive
	* It is unsafe, unnecessary and unpractical to send this many data to the cloud
* It is needed a decentralised, adaptive computational paradigm
	* Data should be accessed locally, so to reduce the access latency
	* This can reduce network congestion and improve scalability
	* Fog and Edge Computing provide faster approaches that enjoy better situational awareness in a way more timely manner
* Edge computing refers to the infrastructure that exists close to the source of data and outside a centralised cloud
	* Its role has been mostly that of ingesting, gather, store, filter and send data to cloud systems
	* A lot of processing can be done on the source of data itself or next to it, at the edge of the network
	* Edge computing significantly improves latency and reduces the volume of data movements
	* It provides new possibilities for IoT applications for those relying on
		* Machine learning for object detection, face recognition, language processing
		* Intermittent connectivity, for instance applications in remote locations where bandwith is expensive or inconsistent
	* It is particularly useful for real-time analytics
	* It improves privacy and security by keeping sensitive data on the source devices
* Fog Computing is a layered model for ubiquitous access to a shared continuum of scalable computing resources
	* It consists of fog nodes residing between end-devices and cloud services
	* Fog nodes are context-aware and support a common communication protocol
	* Fog computing minimises latency
	* It provides local computing resources to end-devices and, when required, network connectivity to centralised services

* Essential characteristics of Fog Computing
	* Contextual location awareness of the nodes and low latency
	* Geographical distribution of the nodes
	* Interoperability and federation of nodes
	* Real-time interaction instead of batch processing
	* Predominance of wireless access
* Fog nodes can be deployed under different models
	* Private Fog Nodes: for the exclusive use of an organization comprising multiple customers
	* Community Fog Nodes: for the use of organizations joined in a community that has shared concerns
	* Public Fog Node: for open use by the general public
	* Hybrid Fog Node: a complex node that is composed of 2 nodes of disticint deployment models, that are unique but bound by technologies that grant data and application portability
* A digital twin is a digital replica of a physical entity
	* It integrates IoT, machine learning, and software analytics with spatial network graphs
	* It creates a living simulation model that is updated and changes as their physical twin changes
	* It is useful for testing and simulations
	* The object that is miirored can be a wind turbine, an engine, an entire airplane,...

# Part 2 - Prof. Salomoni

---

# Introduction
* This module focuses on topics beyond the IaaS model and it is mostly hands on
* The main topics are: cloud storage, Docker containers, authentication and authorization for cloud services, automation for cloud applications
* Professor is also a physicist from INFN, graduated from UniBo

## PaaS
* The PaaS type is a way to program a Cloud infrastructure so to allow developpers to build applications and services
* A PaaS service can include preconfigured features to which cutsomers can subscribe, so to make the system fit their requirements
* The services are updated and maintained by the cloud provider, so the user does not need to worry about these details
	* E.g an Oracle database as a PaaS: no need for the user to update the Oracle software
* PaaS providers can assist developpers in the design of their applications and in the testing an deployment phases
* AWS offers Elastic Beanstalk as a PaaS service
	* It is useful for deploying and scaling web applications and services developped with Java, Python, Docker, and other systems on familiar services such as Apache and Nginx
* There are several PaaS frameworks available, some public and some that can be installed on private resources
	* The INDIGO-DataCloud PaaS layer
	* Cloudify
	* RedHat OpenShift

# Cloud Storage

## File Systems
* Data can be stored directly in a block device
	* In this case data is stored sequentially, and no metadata is stored
* Data can be stored in a database as key:value pairs
* Data can be stored in a file system
	* Data is organised in a tree-like directory structure
	* Metadata such as filename, timestamps, size can be stored also by the file system
* There are many types of filesystems
	* For disk storage there is FAT (File Allocation Table) with several variants (FAT16, FAT32, exFAT), NTFS, HFS, ext2 (extended filesystem), ext3, ext4, XFS, BTRFS (B-tree filesystem),...
* Network file systems allow to access files from remote computers
* Shared file systems allow files to be shared among a set of machines
* The Portable Operating System Interface for Unix (POSIX) standards are a set of standards that define an API and some shell and utility interfaces to maintain compatibility among operating systems
	* It was developped primarly for Unix-like systems, but any OS can use the POSIX standards
	* POSIX emerged from a project started in 1985
	* The POSIX standards are collected in IEEE1003, also called ISO/IEC9945
* POSIX I/O (a non-official name) is the portion of POSIX that defines the I/O interface
	* It provides `read(), write(), open(), close()` and other functions
	* It prescribes a set of metadata that a file must possess
		* The user and group which own the file
		* The permissions that are given for read, write, and execute to different users and groups
		* Attributes such as creation and last modification timestamps
	* POSIX calls can show and manipulate POSIX metadata
		* `chmod` and `stat` are shell commands that provide an interface for the relevant POSIX calls
	* POSIX I/O is stateful
		* Reading and writing data is governed by some persistent statethat is maintained by the OS in the form of file descriptors
		* A file descriptor (or file handle) is a number that uniquely identifies an open file in the kernel global file table
			* The file table contains information such as the inode of the file, the byte offset, and the file permissions
		* Applications cannot read or wirte a file before opening it, so that they can get a file descriptor
		* The position where the next read or write will take place is the position at which the last read, write or seek call ended
		* Write operations require strong consistency: a write call blocks application execution until the system can guarantee that any read call will see the newly written data
		* A dirty solution to stateful I/O is requiring strong consistency for write operations only until the file is written to a memory page, not until the file is permanently stored on disk
			* These memory pages that contain data not yet flushed to disk are called dirty pages, and they are tracked by the OS
			* The use of dirty pages is called page caching
			* The OS flushes asynchronously dirty pages to disk
			* This apporach is POSIX-complaint since the OS tracks dirty pages and returns their content to successive read calls, not the content of the file stored on disk
* A networked file system like NFS is used for accessing files over a network in a way very similar to how local files are accessed
	* It uses a POSIX-like syntax implementing open, read, and write calls
	* Page caching is more complicated in a networked file system since different clients that operate in the same file will not share the same memory pages
	* In general, it is NOT safe to assume that consistency is automatically respected with parallel reads or writes in a networked file system
	* In order to enforce strong POSIX consistency in a networked file system it is needed to enforce that no node can read data until the dirty pages have been flushed to the remote server storing the data: different approaches are possible to enforce this
		* A file system can avoid page caching at all to solve this problem, at the cost of I/O latency
		* It can relax POSIX consistency such that it provides consostency in most reasonable I/O workloads, but does NOT guarantee consistency if 2 nodes try to modify the same part of a file at the same time
		* It can enforce a locking mechanism so that a node cannot modify a file that is open in anothe node
	* NFS relaxes POSIX consistency in order to guarantee a reasonable level of consistency in most use cases
		* It guarantees a close-to-open consistency
		* A file is guaranteed to be consistent from when it is closed to when it is open again
		* While a file is open there is no consistency guarantee: if 2 nodes open the same file at the same time it is possible for them to hold dirty pages
		* It is up to client application to manage concurrent access to the same files
	* Other distributed file systems like Lustre or GPFS implement a complex locking mechanism to ensure consistency

# REST and JSON
* A POSIX interface is not the only possible way to work with files
* REST (REpresentational State Transfer) is an architecture style for designing networked applications
* For all practical purposes, RESTful applications use HTTP GET requests to make calls between machines (create, update, read, delete data)
* Many web services offer REST API
* REST can be used in Python via several libraries such as `httplib, urllib, requests`
* JSON (JavaScript Object Notation) is a lightweight format for storing and transporting data
	* It is commonly used to transfer data to/from web servers
	* Data is organised in key:value pairs
	* Data is separated by commas
	* Objects are delimited by curly brackets
	* Arrays are delimited by square brackets
	* In Python JSON is offered by the `json` module

## Object Storage
* Especially in the cloud, not all the storage is organised with POSIX interfaces
* Object storage organises data into a storage system in self-contained entities called objects
* Each object is assigned an unique ID, managed in a flat index
	* This is contrapposed to the tree-like structure of POSIX file systems
* An object can be accessed by an application by providing its unique ID to the object storage system
* Objects tend to have rich metadata
	* Some of these metadata are non-editable and they are set at the time of object creation
	* Editable metadata can have fixed keys or they can be custom fields
* Fixed-key metadata have fixed keys and allow only the editing of the value field
	* Access control metadata: object storage uses IAM (Identity and Access Management) and ACLs (Access Control Lists) to control the access to objects
	* Content type: also called MIME type, it specifies the kind of data contained in the object
	* Content disposition: it controls the presentation style of the content (automatic opening, fullscreen mode,...)
	* Content encoding: it can indicate that an object is compressed, and the compression algorithm used
	* Content language: the language that the object is intended for
	* Cache control: it specifies whether the object can be cached and whether the data can be transformed
* Custom metadata allow editing of both the key and the value fields
	* They are specified as a key:value pair and they can be added and removed
	* They are limited to a maximum of 100 instances and 10 MB
* A key advatage of object storage is its simplicity
* Object storage system implement only a few commands
	* `PUT`, similar to a POSIX `write`, puts the object into the storage system
	* `GET`, similar to a POSIX `read`, gets the object from the storage system
	* `DELETE`, removes the object from the storage system
	* `HEAD`, returns only the object's metadata
* Object storage follows a write once, read many approach
	* Data is written once, when an object is created
		* Modifying an object means creating a new object: IDs are unique
		* It is up to the user to keep track of which ID refers to which file
		* Since objects are immutable, there is no need to manage concurrent access from different clients
			* Some object storage systems do not allow even to edit the metadata of an object to avoid concurrency problems!
		* An object is uniquely referred to by its ID
			* A simple hashing of the ID can be used to determine the physical location of an object
	* The same object can be read many times
* Objects cannot be used for scratch space or hot storage
* Object-based application are often focused on data archival
* The use of unique IDs allow great scalability, allowing for fast access to a vast number of objects
* It is possible to store vast amounts of unstructured data in an object storage system
* Object storage is used for storing pictures on Facebook, songs on Spotify, and files in Dropbox
* Object storage systems are software-defined scale-out architectures that can take advantage of commodity hardware
	* Scaling out referes to multiplicating the number of equal resources available, instead of scaling up the type of resource
	* I can just add more storage devices to increase capacity, according to demand
* An object storage cluster typically uses a cluster of nodes based on object storage, which communicate to a gateway layer through REST APIs
* Popular cloud storage services based on object storage are AWS S3 (Simple Storage Service), Google CLoud Storage, Rackspace Files
* Some distributed file systems use object storage
	* Metadata is stored in metadata servers
	* Data is stored in object storage servers
	* An abstraction layer provides to users acces to data in a POSIX-like way
	* Examples of this are IBM Spectrum Scale (GPFS), Dell EMC Elastic Cloud Storage, Ceph, Lustre

## Virtual File Systems
* A virtual files system is an abstraction layer on top of one or more concrete storage devices or file systems
* Its purpose is to offer a standardised POSIX interface to applications, so that they do not need to worry about technical details
* Onedata is a virtual file system that provides unified data access across globally distributed environments
	* It allows users to easily share collaborate on stored data
	* It is mostly used for scientific applications
	* Data is organised in distributed virtual volumes called spaces
	* Entities who support spaces with actual storage resources are called providers
	* A zone is a federation of providers which enables the creation of closed or interconnected communities
* MinIO is an high-performance, software-defined object storage suite compatible with AWS S3
	* It allows to mount a remote bucket as if it were a local directory
	* It is the native storage system for Kubernetes
* The fundamental concept is that in a virtual file system I can acces files with POSIX calls, I do not need to prefetch data with HTTP GET requests
	* However, if I want I can use an S3-compatible interface

# Advanced Docker Containers

## Networking
* Docker implements versioning (git-like), component re-use, and sharing through a public repository
* Networking in Docker containers can be handled in several ways
	* Possible options for networking are no networking, bridge networking, host networking, overlay networking, Macvlan networking
	* The networking mode can be specified with the `--network=<my_net>` flag in the `docker run` command
	* Bridge networking is the default networking mode in the absence of a spacific flag
* The flag `--network=none` disables networking for containers
	* It is useful when the containerised application does not need to acces the network
	* In a container run with this option `ip address show` will show only the loopback device
* Bridge networking is the default option for Docker
	* A bridge is a network device that allows the transfer of packets in the same network segment
	* Docker creates a virtual bridge between container and host
	* If 2 containers are connected to the same bridge they can communicate with each other
		* All the containers connected to the same bridge have an IP address in the same network
	* By default, Docker creates a single bridge called "bridge", to which all the containers are connected
	* A new bridge can be created with the command `docker network create my_bridge`
	* The available networks for Docker can be inspected with the command `docker network ls`
	* Containers connected to different bridges cannot communicate with each other
	* In order to connect a container to a custom bridge, I can just specify its name in the flag as `--network=my_bridge`
	* Using different bridges for containers enhances security by making it impossible for containers to communicate with each other
	* Containers connected to the same bridge see automatically all the ports of the other containers
	* In the default bridge there is no automatic name resolution
	* In custom bridges container names are resolved autmatically
		* `ping container1` resolves the actual IP address of container1
	* It is possible to connect a container to more than 1 bridge with the command `docker network connect <bridge> <container>`
	* When connecting to the internet, a container assumes the IP of its host thanks to the NAT service of the Docker engine
* Host networking is specified by the flag `--network=host`
	* This option connects the container directly to the host network, without using a NAT service
	* In this case the container uses the IP address of the host
	* Port mapping is not possiblein host mode, since all the ports of the host correspond to that of the container
	* It is not possible to have 2 containers in host mode running a service on the same port
	* Host networking is used only in special cases
* Macvlan networking assigns an idividual MAC address and IP address to each container
	* No NAT service is used, since the container has its own MAC address
	* With macvlan mode, it is easy to get an IP address exhaustion
	* Also macvlan is used only in special cases
* The networks covered up to this point are applicable to containers running on the same host
* Docker overlay networks instead can connect Docker deamons running on different hosts

## Process Management and Logging
* It is possible to monitor the state of resources from inside a container, but it is more useful to be able to monitor reosources from the host
	* This is especially the case when many containers are running on the same host
* `docker stats` is a live tool that streams container resource usage statistics
* By default a container has no resource constraint and so it can use the host resources for as much as it is allowed by the Docker host kernel scheduler
	* This means that if a container is misbehaving, the host may crash
* It is possible to limit the resource usage of a container with the flags `--memory="256MB"` and `--cpus=".5"`
	* The cpu flag specifies how many cores the container can use: `--cpus=".5"` allows the container to use half of a core
* When containers are running in the background, it is not practical to check its activity live
* The STDOUT and STDERR of a container can be inspected with the `docker logs --follow <container>` command
* Containers can also be managed graphically using the open source tool Portainer

## Best Practices
* In order to increase resiliency and allow for versioning and tracking of changes in software, it is important to use a version-control sistem like git
* Git is a distributed version control system for tracking changes in source code during software development
* A repository is a collection of all the files belonging to a project, including their history
* Development typically takes place in branches
	* A branch is a line of development
	* In git, there is a main branch with the production code called "master"
	* Once a new feature is implemented in a branch, the branch can be merged to the master branch

# Authentication and Authorization Infrastructure (AAI)
* We typically want to protect our data or applications with some form of authentication (AuthN) and with various degrees of authorization (AuthZ) to access them
* The simplest form of authentication to a resource is the use of a local username and password
	* This approach is local: every system stores its own set of credentials
	* In linux local credentials are stored in `/etc/passwd` and `/etc/shadow`
	* This method is definitely NOT scalable
* The resources that we want to protect should have some form of Identity Management System (IdM)

## X.500, DAP, LDAP
* In the early days, an IdM consisted of directories storing "objects" that described generic "entities"
	* One of such directories was basically a distributed database
	* This standard was defined in 1988 and came to be known as the X.500 standard
* The X.500 standard led to the definition of "The Directory"
	* It was a worldwide white page service accessed through a Directory Access Protocol (DAP) through the OSI stack
	* From a common root it was possible to access countries and organizations, and from those more specific groups until single individuals
* In the early 90's, there was a long debate about the adoption of the OSI model or the TCP/IP model
	* The TCP/IP model was supported bu the US Department of Defence and won at the end
	* Now the OSI model is rarely used in practice but is an useful theoretical framework for how applications should work
* With the affirmation of TCP/IP, in order to access the X.500 Directory a simpler protocol than DAP was required
	* DAP was built with the OSI model in mind
* The protocol defined for accessing X.500 from TCP/IP is called LDAP (Lightweight DAP)
	* Despite its original use, it not only allows to lookup information in a directory service, but also for adding and updating it
	* Today nobody talks about X.500, but LDAP is still used!
	* Microsoft Active Directory can be accessed with LDAP
	* In LDAP data is kept in key:value pairs called attributes
	* Attributes are stored in a tree of entries
	* Each entry in LDAP has 3 components
		* A Distinguished Name (DN), an unique identifier
		* A collection of attributes where data is actually stored
		* A collection of object classes: information about the type of entry (a person, a service,...)
	* LDAP is the simplest example of Attribute Authority
		* It is a place where authoritative information about something can be stored
		* We can use DAP to store all the information about the identity of a person (passwords, roles in the organization)
	* LDAP can be used to enforce both authorization and authentication of users
	* In general, LDAP was born for authorization (i.e. storing which users can do what) and NOT for authentication
		* Authentication was implemented later, and every authentication request generates a load on the LDAP server
			* This can be problematic when there are many users or with some application that do not deal with authentication in a smart way

## RADIUS
* Another commonly used protocol for IdM is RADIUS (Remote Authentication Dial-in User Service)
	* A RADIUS server sits between the user and other services: it is an intermediate service
	* RADIUS queries LDAP to assess the identity of a person, but then it can query other services for authenticating it (es. an OTP service)
	* It uses UDP and it is more flexible then LDAP (I can plug-in multiple services to RADIUS), but it is more complex to set up

## Kerberos
* Kerberos is a service that implements strong authentication for client/server applications based on secret-key criptography
	* It was developped at MIT
	* Usually Kerberos is used in parallel to LDAP to manage only the authentication part (while authorization is up to LDAP)
		* Kerberos manages the credentials for different users
		* LDAP stores authoritative information about what users are allowed to do
		* This approach is still widely used in computing and storage resources
	* A client can contact a Kerberos server, which provides a signed encrypted ticket that can be used to access resources
	* The ticket is valid for some time, so this reduces the problem of overloading the authentication server
	* Kerberos is based on symmetric key criptography: the client and the server have a shared secret
	* Kerberos implements a Key Distribution Center (KDC)
		* It is a trusted party between client and server
		* It hosts secrets for all the users of the infrastructure
	* Kerberos is used to implement Single Sign On (SSO) environments
		* A single login unlocks a range of different services
		* In AWS a single login unlocks EC2, S3,...
	* Kerberos has a main issue: it relies on a TRUSTED KDC which holds all the secrets
		* If someone is able to compromise the KDC, then everithyng is compromised
		* This approach is not scalable because it would require mutual trust between different KDC servers: impossible on the internet

## X.509
* From the X.500 standard, a new standard called X.509 was created
* It defines the format for public key certificates
* An X.509 certificate contains a public key and an identity
* Each X.509 certificate is either self-signed (signed by the private key corresponding to the public key included in the certificate) or signed by a Certificate Authority (CA)
* Self-signed certificates are not so trustworthy
* Certificate Authorities are a limited number of organizations that are well-known and act as a Trusted Party
	* They are used for-profit companies, but a notable exception is the non-profit Let's Encrypt
* X.509 is widely used by TLS/SSL protocol, which is the basis of https
* X.509 is also used for authenticating to GRID resources
* X.509 is based on public key criptography (asymmetric cryptography)
	* The public key is known by everyone, while the private key is only known by the key owner
	* The private key should never be communicated to anyone
	* Public key criptography enables encryption (with the public key of the intended recipient) and decryption of data (by the recipient with its private key)
	* It also enables signing of data (nonnrepudiation): I can let others trust that some data came from be by encrypting it with my private key, and showing that it can be decrypted only with my public key
* Http transmission is in clear, and it uses the TCP port 80 (but it can also be configured to use other ports)
* Https transmission is encrypted and it uses the TCP port 443 (but can be configured)

## SAML
* Since now we saw LDPA and Kerberos for authenthication, and X.509 for htpps access, but these approaches are not suitable for authenticating to Cloud applications
* SAML (Security Assertion Markup Language) is an open standard based on XML
	* It allows to share security credentials that can be used for authentication and authorization
	* It is a quite mature standard (from 2005)
	* Its primary use is that of implementing SSO for web applications
	* SAML is NOT well suited for mobile applications (es. to create an API gateway)
* eduGAIN (Global Academic Interfederation Service) is a SAML2-based federation of service providers
	* It enables transparent SSO for members of the research and education community
	* In Italy any service that wants to join eduGAIN must connect to the Italian Federation Identity (IDEM)
		* IDEM is managed by GARR
* In Italy since 2013 SPID (Sistema Pubblico di Identità Digitale) was created as a SSO for citizens towards public institutions
	* SPID uses SAML2
	* There is a discussion about how SPID and eduGAIN/IDEM should interoperate, also because universities are public institutions and therefore should offfer their services through SPID
* Multi-Factor Authentication (MFA, also called 2FA) access to a resource is granted only after multiple credentials have been presented
	* It is a widespread practice used for increasing security
	* A best practice is to use MFA whenever using a service connected to the internet (especially for services holding private data)
	* MFA works by combining something that you know (password) with something that you have (an OTP, fingerprint, email address,...)

## OAuth and OpenID Connect
* In order to authenticate and authorize services in the cloud, 2 newer protocols are used: OAuth and OpenID-Connect
* OAuth is an authorization framework and does not deal with authentication
	* In OAuth an access token states the authorization rights of the client
	* SAML is typically used for enterprise SSO of web applications, while OAuth is designed for the authorization of generic applications or resources on the Internet
	* OAuth can be used for web applications but differently from SAML does not assume that the client is a web application
* In OAuth there are several roles
	* Resource owner: a user that own resources hosted at a service
	* Client: an application that wants to access resources
	* Authorization server: a service that authenticates user and client and issues access tokens accordingly
	* Resource server: a service that holds protected resources and grants access based on access tokens
* The first interaction of a client with the OAuth server involves the registration of the client
	* During the registration a client receivs an id and a secret
* OpenID-Connect (OIDC) handles authentication of users in the cloud
	* It is a simple identity layer on top of the OAuth protocol
	* It allows clients to verify the identity of an end user based on the authentication performed by an authrization server
	* It allows clients to obtain information about an user in an interopaerable REST-like manner
	* OIDC returns information on who an user is and how it was authenticated using an ID token
		* The ID token is a JSON Web Token (JWT)
* OIDC/OAuth is used in most web services like Google, Facebook, Microsoft, GitHub
* JSON Web Token is an open standard for securely transmitting information as JSON objects
	* JWT are usually signed and, if required, encrypted
	* A JWT contains an header, a payload and a signature
	* The header and payload are converted with base64 encoding
	* The signature uses an hashing algorithm to combine header, payload and a secret from the signer
	* If the signature does not match the content, the JWT is rejected
* Why to prefer OAuth, OIDC, and JWT to other solutions?
	* They are widely used, standard, not bound to any specific authentication system
	* They are scalable since they rely on distributed verification of access and identity tokens
	* They are driven and developped by industry, not research
* In general, for the Cloud we want an AAI twith certain characteristics
	* Open Source and uses widely adopted standards
	* Supports for enrollment and registration of users (and optionally self-registration)
	* It is able to link various credentials to a single identity
	* It is flexible: it should be possible to grant administration priviledges to users, add users to groups, manage membership requests, and edit user information
	* It is able to expose user and group information to applications that request them
	* Supports full auditing: keeps track of security events for legal and logging purposes
* Since OAuth/OIDC was developped by the industry, it does not completely fulfill the checklist of requirements of academic institutions
	* There is a trend in acedemia to develop AAI systems that extend the standard protocols

## INDIGO-IAM
* INDIGO-IAM was developped at INFN and implements SAML, X.509 and OIDC
	* Authentication is flexible: SAML, X.509, OIDC, or username and password
	* Accounts can be linked
	* It is a concrete implementation of the several protocols seen so far
* The authorization workflow with IAM for a web application
	* A web app integrates with IAM to delegate user authentication
		* OAuth and OIDC provide the authorization code flow for this process
	* An user accesses the web app, that redirects back to IAM for authentication
	* The user does not have a valid session on IAM, so a login page is shown
	* The user logs in with one of the external providers (Google, eduGAIN) or with username and password
	* If the user chooses an external Identity Provider (IdP), he is redirected to the relevant login page
	* The home IdP (for the user) authenticates him and sends back an authentication assertion to IAM
	* IAM validates the assertion, and shows a consent page for authorizing the web app to obtain information on the user
	* IAM generates an authorization code and sends it back to the web app using http redirect
	* The web app shows to IAM its authorization code and receives from it an access token and an id token
		* In IAM these tokens are both JWT tokens
		* The access token provides mainly authorization information
		* The id token provides mainly authentication information
	* IAM validates the tokens following the OIDC protocol
	* The application can request additional information by quering the `/userinfo` endpoint and presenting the acess token
	* IAM returns a JWT with content that can partially overlap with the id token


# Cloud Automation
* Cloud Automation is a set of processes and technologies that allow to automayte several operations related to cloud computing
* Automation is tightly linked to reproducibility

## Microservices
* Microservices are a way to build applications as a collection of many small autonomous services
* They are contrapposed to the old monolith architecture
* Microservices are like cattle, while a monolith application is like a pet
* In an organization, each microservice can be managed and developped by a specific team, which operates in an autonomous way and is responsible for the service
* In a microservice architecture multiple independent processes communicate with each other through the network
* Differently from monoliths, in a microservice architecture states are external to the application
* In a monolith a business is organized as 1 large team per tier (backend, frontend, database)
* With microservices there is a tendency to have 2 pizza teams (a team that is small enough to order only 2 pizzas) composed of people from different backgrounds (backend, frontend, database) that work on a specific task (orders, shipping, catalog)
	* Each team is directly responsible to the end user for its service
* Databases tend to not be monolytic but split: I have an account DB, an inventory DB, a shipping DB
* Communication between microservices are typically done with REST APIs
* Microservices are not perfect and sometimes a monolyt is preferrable
	* Deployment is more complex since each service must be deplyed independently
	* I need to worry about the orchestration of the services
	* There are more services to monitor
* However, microservices offer several advantages
	* They are more reliable, since there is no single point of failure
	* They are more scalable horizontally
	* Scaling can be granular and involve only the required components, and not necessarily the entire application

## DevOps
* DevOps (Development Operations) is a pattern developping scalable and applications where development and operation are tightly integrated
* Instead of developping a production-ready application and deploying it, I follow a tight release and feedback schedule (release early, release often)
* The continuous feedback allows to avoid unnecessary work and create something that the users will like
* The main principle is to involve the end users in the project as early as possible
* It uses a set of tools and processes to facilitate automation, monitoring, and continuous integration
* DevOps is an example of risk reduction in software development
* It is typically applicable to distributed microservices-based applications

## Continuous Integration, Deployment, Delivery, Learning, Monitoring
* Continuous Integration is a software development practice where developpers frequently merge their code changes to a central repository, after which automated builds and tests are run
* This approach produces deployment packages that can be used for deployment to multiple environments
* Jenkins is a widely used tools for this scope
* Even with interpreted languages that do not need compliation (Pyhton) it is possible to implement continuous development with automatic Quality Assurance tests
	* sloccount is a tool that counts the actual lines of code in a project
	* pylint is a static code analisys tool that looks for programming errors and helps enforcing a coding standard
	* pytest and nose2 are tools for writing tests for code coverage
* Continuous Deployment refers to the capability to deploy applications to a pre-production and production enviroment through automation
* Continuous Delivery is a development practice where code changes are automatically built, tested, and prepared for release to production
	* The main aspect of Continuous Delivery is the automatic release to production, which extends the framework of Continuous integration
* Continuous learning involves a continuous feedback and improvement
	* Applications should be built with monitoring, auditing, and telemetry in mind
	* Telemetry is the remote monitoring of something
* Monitoring should start in the development phase, using the same tools adopted in production to spot problems before they hit the users
	* Monitoring refers to application performance monitoring and server monitoring
* A regular baseline for monitoring should be acquired, and metrics over a period of time should be compared to it
* When scalable, reliable, and maintainable applications need to be deployed to the cloud, it is important to find a way to instantiate the resources needed by the application

## Container Orchestration
* Containers are excellent for the creation of a microservice architecture
* We saw already `docker-compose` for creating an application stack on a single host
* Container orchestration instead refers to orchestrating many containers across distributed hosts
* Docker Swarm is a simple way of orchestrating containers with Docker
	* It is integrated in the Docker engine and does not require additional software
	* It is decentralised: each node in the swarm can assume any role at runtime
	* It scales automatically according to load
	* It supports desired state reconciliation: if something happens to a Swarm cluster, it tries to bring the cluster back to its optimal state (if a container crashes a new one is istantiated)
	* It supports multi-host networking thanks to the use of an overlay network
	* It has service discovery thanks to a DNS server embedded in each Swarm
		* The Swarm manager discovers services and assigns to each of them a unique name
	* It supports load balancing across nodes
	* It is secure since all the communication across nodes are encrypted TLS
	* It supports rolling updates and allows for rollback of tasks
* An overlay network is a way in which Docker can handle networking
* A Swarm service is the definition of the tasks to be executed on a Swarm cluster
* Defining a Swarm service means describing its optimal state
	* How many replicas I want for the service
	* Which storage resources should be available to it
	* How it connects to the network
	* Which ports should be exposed
* Any node that is part of a Swarm cluster can still run regular containers in addition to Swarm services
* Differently from standaone containers, it is possible to modify the configuration of a Swarm cluster without bringing down the service
* Docker Swarm services are persistent, while the load balancer is not

## Docker Secrets
* Writing and persisting application data for containers is not so simple
* If I need to include a password or other sensitive data, I cannot store it in clear text in my docker-compose file, especially if I want to syncronise this file to a public CLoud like GitHub
* Docker provides secretes for storing sensitive data that should not be transmitted over a network
* Secrets are only available to Swarm services, not to standalone containers
	* They are encrypted at rest and only made available to running Swarm services that have been granted explicit access to them
	* They are never stored in clear text and only made available to Swarm services in memory (or in a RAM disk)
* If I want to use secrets in a standalone container, I can just create a Swarm of scale 1
* Secrets should be used for usernames, passwords, ssh keys, and other important data

## Swarm Configs
* Non-sensitive information such as configuration files do not need to be stored in encrypted form
* Docker provides for this scenario Swarm configs
* They are like secrets but are not encrypted and they are not stored in RAM, but mounted directly into a container's filesystem
* Like secrets, also configs are only available to Swarm services and not to standalone containers

## Kubernetes
* Kubernetes (K8s) is another popular container orchestrator
* It is open source and backed by Google and RedHat
* A Kubernetes cluster is composed of a Master that coordinates the cluster and Nodes that run applications
* A pod is the basic building block of Kubernetes and it represents a running process on a cluster
	* It encapsulates an application container, storage resources, a network IP and options that govern how the container should run
* The most common Kubernetes use case is that of a pod running a single container
	* In this case the pod can be thought of as a wrapper around the container
* A pod can also run multiple containers that need to cooperate
	* It can encapsulate a multi-container application
	* The pod in this case wraps the containers and the storage resources in a single manageable entity
* A kubernetes service is an abstraction that defines a logical set of pods and a policy by which to access it
	* Pods have IP adresses but they are not exposed outside of the cluster
	* Services on the contrary allow applications to receive traffic
* Deploying a Kubernetes cluster is not trivial, and because of this many clouds provide an already-configured Kubernetes cluster on which I can deploy my containers
	* This is known as "Kubernetes as a service"
	* AWS provides the "Elastic Container Service for Kubernetes" (EKS)
	* A Kubernetes cluster is composed of a control plane and a data plane
	* The control plane includes the masters, while the data plane includes the worker nodes
	* EKS provides a managed control plane that is automatically updated with new releases of the Kubernetes software
