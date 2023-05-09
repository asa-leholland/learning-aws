# VPC Endpoints Introduction

VPC allows you to privately connnect your VPC to otherAWS services, and VPC endpoit services

- eliminated the need for for an Internet Gatewya, NAT fevice, VPN conection, or AWS Direct Connect connections
- Instanaces in the CVPC top not require a public IP addess to communicate with service resrouces
- Traffic between your VPC and other serviecs does not leave the AWS networkr
- Horizontally scaled, redundant, andhighly availbae VPC component
- ALlows secure communcaition between instances and services - wihtout adding avaiablit risks or bandwidth constrant n your ftraffic

Ther are two type sof VPC ENdpoints
 - Interface Endpoints
 - Gateway Endpoints


The Internet, without VPC Endpoint

connects to the endthe Gateway to enter the VPC, then connects bia a Router to a VPC Endpoint ot hte S3 Bucket



## Interface Endpoints

These are Elastic Network Interfaces (ENI) with a private IP address
THey serve as an aentry point for traffic going to a supported service

Interface Endpoint are powered by AWS PrivateLink

Access serviess hosted on AWSeasily and sercurely by keeping traffic within the AWS netowrk

Pricing per VPC endpoint per AZ 0,01#hour -> about 7.5$ monthj

Interface Endpoitns support :
API GateWay
CloudFOrmation
CLoudWatch
Kinesis
SageMaker
Codebuild
AWS Config
EC2 API
ELB Api
AWS KMS
Secrtes Manager
Security Token Service
Service Catalog
SNS
SQS
Systems Manager
Marketplace Partner Srevices
Endpoitn Serviec in other AWS Accounts



## Gateway Endpoints
A Gateway enpodint is a gatehawa y has a taarget for a specigfiic route in your route table, used tfor traffic destined for a supported AWS service
To cereat a Gatewyu Endpoint you must specigy the VPC in which you want to create ethe endpoint, and thservie eo twhich you want toe esabligh the conection.

AwS Gateway endpoint sucrreunlty only suppoerts 2 services (Aamazon S3 and DYnamoDB()



## Cheatsheet

VPC Endpoint ahlep keep trafgfic between AWS services within the AWS NEtwork
Two kinds: Interface Endpoints and Gateay ENdpiints
 INterface cost money ,Gateway ENpoints are freee
 Inferfave ENdpoints use an elastic Network Interface (ENI) with PRivate IP (powered by AWS PrivateLink)
 Fateeay eNdpoint si a targe for a speicifg ooutr in your reout table
 Interface ENdpoits supports many AWS servies
 Faeway Endpoit only support DynamoDB ad S3

