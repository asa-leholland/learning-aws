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

