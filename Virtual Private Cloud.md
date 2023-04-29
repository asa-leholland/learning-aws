# Virtual Privat Cloud (VPC)
Provision a logically aisolated section of the AWS cloud where you can luanch AWS resoruces in a virtual network that you define

## Core Components
Think of AWS CPC as your own persianl data centera
ives yo ucompelte control over your virtual networking evnironent

AWS ACCount
- Region
  - VPC
    - Availability Zone
      - Public Subnet
        - EC2 instnce
      - Private Subnet
        - RDS DB
    - NACL Route Table <-- Router <--- Internet Gateway <--- The Internet


Internet Gateway - IGW
Virtual Private Gateway (VPN Gateway)
Routing Tables
Network Access Control Lists (NACL) - Staeless
Security Griups (SG( Stateful
))

Public Subnets
 Private Subnets
 Nat Gateway
 Customer Gateway
 VPC Endpoints
 VPC Peering




 Key Features

 VPCs are Region Specific - they do not span regions
 You can create up t 5 VPC res Region
 Every regio comes with a default VPC
 You can have 200 sunet per VPC
 You can use IPv4 Cidr Block and in addition to a IPv6 Cidr Blocks - adddres of the VPC
 Cost nothing - VPCs Rout eTables NACLS Internet Gateways - Securiy Groups, subnets, VPC Peering
 Somethings cost money - eg NAT Gateway, VPC Endpoints, VNPN Gateway , Custoemr Gateway
 - DNS hostnames - shoudl you instance hav e domain name addresses


IPv6 Cidr Block : 2600:1fjs1:9120:812dd00::/56

SNS resolution is Enabled and DNS hostnaes re Disabled by defalt


AWS has a deafult VPC in eery region tso that you can immegiately deploy isnatnces

- Create a VPC with a size /16 IPv4 CIDR block (172.31.0.0./16)
- Create a size /20 default subnet in each Availability zone
- Create an internet gateway and connect it to your default VPC
- Create a default seciurty group nd associatet it with your default VPC
- Create a default nwtwok acces control list (NACL and assocaite iwt wht your default VPC
- Associate the default DHCP options set wfor your AWS accout with your defautl VPC
- When you crate a AVPC it automaticaly has a main route table
-
- )



0.0.0.0/0 is also knwwn as default
It represnts ll psssible IP addresses

When we specifiy 0.0.0.0./0 in our rtoue tabel tfor IGW we are allaoring internat access
When we specify 0.0.0.0./0 in our secruriy groups inbound ruels, we are allowing all traffic from the internet access our palic resources

When you see 0.0.0.0./0, just hitnk fo givign access from eanywhere or the internet



VPC Peering
- allows you to connect one VPC with another over a direct network route using private IP addreses
- - instances on peerred VPCs behave just like thaey are aon the same netowrk
- Connect VPC s across soame or different AWS accoutns and regions
- Pering using a Star Configuriotn : 1 Central VPC and 4 other VPCs
- No transifitve peering - peering mu taek palce firecl betwee n VPCs
- Needs a one to one connection to immeaite VPC
- No Overallppitn CIDFR Blocks


Route Tables
- sued to edterine where netweokr fraffic is directed
- Each subnet in your VPC must be asscoaited with a route table
- A sunnet can onl asooicated with one route table at a tie, but you can asscoaite multiple subnet with the same route tabel


Internet Gateway - IGW
The Internet Gatewy allows yor VPC access to teh Intenret
IGQ does two things
1. provide a target in your PVC route tables for internet - routable traffic
2. perform network address transaltion (NAT) for instance that have been assigned peublic IPv4 addresses


The Internet --> IGQ (Internet Gateway)--> Router --> Route Table --> Target (igq-id) -> 0.00.0.0.0.
To rouute tout to the interent you need to add in your route talbes tyou need access a route to teh Intergnet Gateewya and set thte destination t o be 0.0.0.0./0


## Bastions/ Jumpbbox
Bstions ar eEC2 instances which are security hardedn
They are desigend to help you gain access to your EC2 Insatnces via SSH or RCP that are in a private sunet

They are also kowns as Jump Boxes wbecasue yo are jumping grom one box to aothers
NAT Gateways/Instances are only instende for EC2 isntacnces fr ros hitngs suhc as securit updates
NATs scannot should not be used as Basatios

System Managers Sessions Manager repalced the need tfor basions

Bastion exists on the Public Subnet withi nteh Eailability Zone and allows access to a n EV2 instance, which sends data to a NAT Gateway and out put to the internet be orereeturning


### Direct Connect
AWS direct connect is the AWS solution for establighin dedicatd network connceiton from on-premisies locatios to AWS
Very fast nnetowrk - lower abadndwith 50M-500MM or higher bandwitdht 1GB or 10 GB
 helps reduce netwrok costa ns dincreae bandwidht htrouput  -great for high traffic networks
 Provides a ore consistnt netwrok expierenc than typical interneg based connectios
 AWS Direct Connect Location - connects OnPremise Rotuer with AWS Cage and eventually the AWS Cloud (VPC and private sibsnet)


 ### Auto Scaling Group
 Auto Scaling Group Introduction
 Set scaling rules which will autoatciall launch additional EC2 instance of shutdown instance sot meet current demand


 ASG cotnains a collection of EC2 isntances taht are treated as a group for the purpsies of automaticaly scaling and manageerment

 Automatic scaling can our via
 1. Capcaity Seteigns
 2. Helathc HCek repalcements
 3. Scalaing polciies


Simplest way tos work with ASGs ins to euse the capacity settings - desired capacity, min and max

Min is how amny EC2 instances hould at least be running
Max is number EC2 insacntes llaowe s to e running
Desired Capaicry - is how many EC2 instances you wante o ideally run
ASGawi ll always launc insces to meet minium capciaty

Min is how many should at elast be running
Ma xi max allowed o be runnign
Desired Capacity his how man instances you want ot ideally run

ASG will awlyas launch isntances to meet minimum capcity


EC2 Health Check Typ - ASG will perform a health check on EC2 isntance s to determin if ther is a softwre or hardware issue. Thisi si basdeod nthe EC2 statsu Checks. If an isnatce is conisdered unhealthy  ASHG will termiante and launch a new instance

ELB Chekc - ASG will perform a health check base on the ELB helath chceck. ELB can perform health checks by piing an HTTP(S) enspoint with an epected reponse. If ELB determine a instance is unhealthy it fowarfs this information to SAG which will terminate the unhealthy instance. - requriee making an HTML hrealth check get 200 OK

Scaling Policeis
- Target Tracking Sacalig Polciy
- Mainiantains a speciif cmateric at asarger value
- If Aerage CPU Utlilziation exceed s75% then add another server
- Scaling Out = addign more instance
- Scaling In - removie ng instanes

Scaling Policies can be

Applciaton Loa baalcner Rewuqst Count per Targe
Average CPU Utilized
Average Network In (Bytes)
Nevegare Ntwtowkr Out (Bytes)

Simpel Sacling Polciy - scales when a n alarm is breached
Create scaling Polciy
 name - NLSD

 Excecute polcu when

 Not recomemmdendn - egacly lecgacy scalign polcu using scalig polciye with septes nwps


 Scaling Polciieys with Steps
 Scales when a n alarm is breached - can escaelared based on alarm calue cahgneing

 Take an ciont - Add X instances when X <= Successgul Buidls < 3


 ASG-ELB Integration
 ASG can be associaetd with Elastic Load Balnacer ELB when ASH ig asscoiate with ELB richer health checks can be set

 Classic Load Balacers are asccoiaes deirectl yo ASG

 Classcic Load Balancers

 Application and Netwok Load Balancers are assocaited indeitely via tehir Targe Groups


 ASG Use Case
 1. Busr of atraffice wfrom the internt hits the fomain
 2. Route53 point sthat traffic t oour laod balanceer
 3. ut load balancer ppasses the traffic to the target gorop
 4. The target group is associated with our ASG and sends the traffic to instance sregistere with our ASg

The ASG Secaling Pocly will check ig thour isncatea are nreat avapiar
The sacling polcu determine we need antoerhe iansnct and tit laucnhes an new EC2 sintace nwith the associate Launch Configuration wo oout AS


## Launc HCofngiruatin
is an isntace confiuration tempatlet that an Uaoscalign roup uses otl aucn EC2i sntaces

A lucn hconfigtion is the same pcorss oas lancug an EC2 isntance except you are saving that config to Launch an Insance tofr lAte

These cannot be edited - when you need to update a luanc configutation you creat the new one or closne the exitin gconfgriton tand then manually assocaite that new launch confriton
Launc htemptlest re Launch veondifutaoi onwith Verions ing - aeveryon spppaear to still use launch fonciguriotn

ASGs

An ASG is a collection of EC2 insatnces grouped for scaling anadm anagement
Scaling Out is when adding serer
Scaling In is when you remove servers
Scalign Up is hwne you increase the size of an isntce - eg. updating Lucn confguation iwth laucrger size
Size of an ASG is based on mIn max and Desired Cacpaity

Target scalign polcy scales based onweh ena tage maalue sfor a metric is breahce eg verrage UCCPUS uilzieation ecreed s75%
Simples caling piocu tggers ac scaling when a n alarm is breached
Scaling paoc with Steps is the new cerioons f simples caling polc and allwos you to created steps basd on eculsition alrmar values
Desired capcaiy his how amny Ec2 isntance yo uwant to ideaalyl reun
An aSH wil awys wlanhces intance tom eet minimu capacy
Ahealth cehcks detemien the urent ato f hanisnat to n the ASh
Halht chehcks can be reun afiangst iether a EL Bor the EC2 isntances
WHne a na utomascaling saunch a n sisntani it sues a Laucnh OCnifutioan which hiodls the conigutoiatn valeus for hteat neew sinstance eg. AMI , INstance Tpye or Rle
LAucnh COnguration ation canot be edited and must be closed or a ew one created
Launc ocnugriaont msut be maually uspadte by audedi tn teh Auto Scaling iseettig
s
