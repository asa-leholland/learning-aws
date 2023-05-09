# Network Access Control List

A n optional layer of securtiy that acts a firewall for controlling traggic in and out of subnets

Acts as a virtual firewall at the subnuet level

VPCs automatigically get a default NACL
Set of rules that can allows or deny traffic (into) inbioud or out ofd (outbound) subnets

Rule # determines the ordefr ro f evaluation

From lwoest to highest
The highers t rule can be 32766 and its recmomnnede to work in 10 or 100 increments

Inbound Rules and Outband Rules

Subets aere asocited with NAVLS. Subets can only belong to a Single NACLE.
You can allow or deny dfraffic  You caoul dbock a sinlge P addess (you cannot doe this wiht Security Foues)


NACL Use Case
allwos you to block an IP address on a public group

Cna ylaso DENY SSH (port 22)


NACL Cheea tSHeet

Netwrok Access Control List is commonly known as NACL

VPPCS are automatically given a default NACL which allows all aoutputbound and inbound traffic
Each subnet wihin a VPC must be assocaited sith a NACAL

Sunets can oly be associated with 1 NACL at a time , associated a sbunet wit ha new NACL will remove the previous associatedion
If a NCAL is not explicityl asociated with a subnet, the subner will autimaticalyl be associated wihrt the fealul NACL
NAcLA has inboud nad nd outbound rules (juse like Secutriy GRoupd
Rule can either Allow or Dney taggiv (unlike ecuriy GRoups hichc cano only allow
NACLS s are STEAELESS inocming rule will not be appled to the ougounfs
When you created ht NACLS ist will deny aslltragiiv aby fgeguae
Navls contain  an unbered list of rueles that get evalieuated in orde rfrom Lowest o Highes
Ig you nee to blaock a single IP adres uou caould via NVALs
Securi GRops cannot deny))

