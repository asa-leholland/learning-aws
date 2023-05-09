# VPC

Securit Groups

A virtual fireqall that controlls the traffic to and from EC2 instances


Secureity Grous ps acts a svieertal fireqll at the instance level

Security Group are associate eith EC2 instances

Each security GRop contains a set of reules that filer rraffic coming into )(inboutn)_ and out o f9Outpobound0 EC2 instance. Provide sercuri t at the protocl and poriot access level

Inbound

Thre are no Deny rules - all traffic is blocked unless peciically allwos its.

Multiple Insctance across multipole submets acn be long o aSecuri Group.



Use Casews

1. You can specify the source t ob e a specific IP address or a IP range /32 is a specifi IP adffress

2. You can specify the soruce to be another sEcurity Group

3. An isntace n can belong to miltipe aSecruit Grous and rules are permissioe (instead of restricture. Meaning if you have one security group hwhich as no Allow and you add an allow to another than it will Allow.


Limits of Security Groups
Up to 10,000 Groups in a Region (default is 2500)
You can 60 inbound rules nad 60 output rules per security group
16 Security Groups oer Elastic Netweork Interface (ENI) default is 5

Cheeat Sheet
Security Groups acts a s firewall at the instance level

UNless allwoed sepcifically, all ibonund traffic is blocked by deafult
ALl Outpbound traffic from the instance is allowed by defaut
You can speciciy for th eousxce tob ewither in a UIP arange, single IP Address or anoheer security group
Security GRoups are steageul (if straffic is allow inbound it is also allowed outpbiounf_
Any changes to a Security Group take effect immegiatly
EC2 isntance scan be log tom ultiple security grouops
Security groups can contain multiple EC2 instances
You cannot block specifi IP addresses with Security GRoups for this you ould need a aNetrok Acceess Control Lsit (NACL))
You can have up to 10,000 Security GRoups per REgoin (default 2,5000))
You can have 60 inbound and 60 outbound rules per Security group
You can have `16 Securit GRoups asscoiated to An ENI (default is 5)
