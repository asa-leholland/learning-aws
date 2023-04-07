# Elastic Container Service

ECS is a docker-managmenet service - scalabale way to run containers (orchestration service)

ECS - Cluster - groupig of EC2 instances which house the docker containers

Task Definition - JSON that defines up to 10 containers containsers you want to run

Tasl - a container that only runs for the duration of the workload (one-off jobs)

Service - intended for long running applications (Django)

Container Agent - binary n each EC2 instnace

ECS Cluster is made up of multiple EC2 Containers, each which have Services and/pr Tasks


## Creating an ECS Cluster

Create Cluster - "FarGate" or "ECS Cluster" - networkign components

Use Spot or On Demand - ECS can save money with Spot - background tasks can be interrupted

EC2 Instance Type
Number of Instances
EBCS Storage Volme
EC2 can be Amazonf Linuz 2 or Amazion Linux 1 (both have Docker)
Cjoose a VPC pr create a new VPC
Assign an IAM Role
Option to turn on CloudWatch COntainer Insights (metrics on container operation)
*Choose a Key Pair - this is for ssh in (generally not recommended)


## Task Definitions File
Create new
Docker images provided via ECR (Elastic Container Registry) or DockerHub
You must have one "Essential" container - if this fails or stops then all other containers are stopped

AWS has wizard to create Task Definitions File


## ECR
Allows user to store amanage and deploy Docker container images


Docker Image uploaded to ECR ----> Accessible by ECS (Elastic Container Service), Fargate, or Elastic Kubernetes Service (EKS), or On-Premise

Fargate: Price based on task size - requirs netwrok mode awsvpc
AWS-managed infrassturcutre - no Amazon EC2 instances to manage

EC2: Proce based on resource usage - multiple network modes available
Self-managed infrastructure using Amazon EC2 instances

Task Roles -


T2 Micro - 500 MIB and 1 vcpu for the free tier

Host Port (what uses to connect to internet): 80
COntainer Port (what used to start p the applicatin): 8080
TCP protocol

ECR will requie IAM Role


Required Roles for IAM
ecsTaskExecution - AmazonECSTaskExecutionRolePolicy
ecsInstanceRole - AmazonEC2ContaienrServiceforEC2Role

LoadBalancer - not needed

