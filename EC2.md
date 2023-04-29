# Elastic Compute Cloud
EC2

Clous Computing Service
Choose your OS, Storage, MEmeory, Network Throughput
Launch and SSH into your server within minutes

EC2 Instance Types and Usage
General Purpose - A1, T3, T3a, T2, M5, M5a, M4
- balance of compute memoery, and netowrking resources - use cases: web servers and code repos

Compute Optimized = C5 C5n C4
ideal for compure bound applications that benefgi crom high performance processor
use cases: scientific modeling, dedicated gaming servers, and ad server egnies

Memory Optimized: R5 R5a X1e X1 HighMemory z1d
fast performance for workloads thart process large dat sets in memoerry
Use cases: in-memory caches, in-memory darabaes, real time big data analytics

Accelerated Optimized -> P3 P2 G3 F1
hardaare accealaertors or co-processors
Use acases: machin elaerning, computation la finance, seismaic analytis, speech recognizieoint

Storage Optimized: I3 I3en D2 H1
high squential read anad write access to very large dat asets on local storage
Use cases: NosQL in memor  or transacaiontl databases, fata warehousing

# Instance Sizes
Generally double in price and key atrributees


Instead od embedding AWS credentials (Access Key and Secret in your code ) so your insatance has permission to access scertian servies, you can attach a role to an instance via an Instnace Profile

You want to always avoid embesdding yor AWS credentials when possible

You:
1. Create an IAM Policy
2. Assign those police to an IAM Role
3. Put that IAM Role inside an Instance Profile
4. Attach a role to an EC2 isntance cia an Instance Profile

THe Instance Profile holds a reference to a role. THe eEC2 instance is assocataie ith the Intnace Proifle. WHen you select and IAM reol when Launchig an EC2 instance, AWS will autoamtically create the instance Profiel for you. Instance Profile ars are not easily viewed via the AWS onsole.

## Placement groupsPlaacement groups let you choose the logicl palcement of your einstances otto optimize for communication, performance or durabilityPlacehment groups are re.CluLCLt

.-
 packs instances close togherth inside an AZ
 low-latecy network performance for ighly coupled ode - to nodde communnicnan
 well suited for High Perfocamce Coumputing (HPC)
 Clusters cannot be multi-AZ

 Partition
 - spreads instances across logical partitions
 - each partiiton do not share the underlyig hardwate with each other (rack per partitio0
 - well suited for large distriuted and replicated work lofads (Hadoop ,Cassandra, Kafka))

Spread
- Each instance is placed o na different rack
- When critical instances should be kept separte from each other
- You can spea a mza of 7 instances. Spreads can bem ulti-AZ

You can prvode an EC2 with UserData which is a script that will acutomatically run when lanudnchig nan instance. You aould isntall package, apply update or anthing

From within the EC2 instance, you can ssh in CURL this URL you can see the usr data script
curl `192.254.169.254/latest/user-data`

EC2 Metadata
- additioal info you can receive about the EC2 instance at run time
- From within EC2 - 169.254.169.254
- latest/meta-data
- public-ipv4 - the current public IPV4 address
- ami-id  - the AMI ID used to launch this EC2 isntance
- /isntance-type - the instance type of this EC2 instance
- Combine metadata with () all sorts of advanced AWS eatures


elastoc Compite Cloud (EC2) is a cloud computig nser vice
Condifure your EC2 by choosing your OS, Storage, MEmory, Netwrok Throughput
Launch and SSH into your srver within minutes
EC2 comes win variet y of instance types specialized for different roles
    Genral Purpose - balance of compute, memory and netwokrig reources
    Compute Optimized - Ideal for conpute bound applications that benefit fro high performacen cprocessor
    Memroy Optimized - Ideal for comptue bound applications that benegift from high performance processor
    Mmory Optimized - fast performanc wfor workloads that process large dara sets in memory
    Acceleatioed Optiized - hardware accelerators or co-processors
    Storage Optimized - high, sequential read and writ a access to very large fdata sets on lcoal stoage

Isnatnce Size generally double in price an key attibutes
Plachement Gourps let you choose the logical palacehement of your intstance sto ipoptimize for communication perfoarmce or duavlt. Pkacehment groups are free
UserData - a script that will autoamtically run when launghing an EC2 isntace
MetaData - etaa data bout endpoint when you SSHd into teh EC2 inace - get the isntance tpyke currnet addes
Instance Profiel - a container for an IAM rol that yo ucan use to pass roel nfromation ot and e