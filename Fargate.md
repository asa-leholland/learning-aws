# ECS Fargate - or Fargate
Under the ECS Cluster
no EC2 provisions - then launch Tasks as Fargate
You no longer have to provision consifute and scale cluasters

You pay based on duratio and consumption

AutoScaling GRoup

ECS Cluster
EC2 Container
Task Task Task Service

EC3 Contaier
Service Service



Fargate is a single ECS Cluster with all the tasks and Services (inside of an ASG)

Define memory and vCPU
memory - 30GB and 4 vCPU

Then need to add contaienrs and allocate the memory and vCPU required for each
Even though this is a serverless container, you do can choose what VPC and subnet it will run in (VPC is virtual private cloud)
Can Apply Security Group to a Task.
 - Would you apply the Group to the EC2 container the actual server or would you apply the Group to the task?
 - Always apply at the Task level
 - Can Apply an IAM Role to the Task - can apply Security GRoup and IAM Role for both ECS and Fargate Tasks and Services



## Fargate vs Lambda
Both serverless compute services
Fargate - runs as long as you want ith memory up to 30 GB (more manual labor, You provide your own containers)
Lambda - 15 mins max, up to 3 GB RAM,only standard containers, Pay per 100 ms
Both Fargate and Lambda have Cold Starts
Lambda - very streamliend to integraet

Lambda per 100ms

### Fargate

Take a Docker image (for ECS and Fargate)

Fargate is ECS

Create a new Cluster - create a "Networking Only" (AWS manages the EC2 instances for us)
Do not create a VPC

Need to Create a Task Definition
- Needs ecsTaskExecutionRole
- awsvpc
- Task Size: task memory is 0.5GB
- Task CPU (vCPU) is 0.25 vCPU

Need to Add Container
- copy paste image link from ECS
- Memory Limits: 128MiB
- Add Port mapping: 8080
- When you select awsvpc in Task Definition, you must make Port 8080
- set environmnet variables for PORT (8080) and NODE_ENV (productioN)

Once you have created a Task Definition, Added Container - then create the Cluster
Then once Cluster is created, need to go to Services and Create a new Service using the TaskDefinition.
Configure Service using:
- VPC and Security Group:
  - Need to select a cluster VPC
  - Need to select a subnet (you might not think you need one since this is running serverless, but you do)
  -  Can opt out of Load Balancer
  -  To run, get the Cluser -> Fargate Cluster -> Task
  -  Inside the Task, you will need the Public IP under Network, then run that using your defined port (8080)

By default, the port inside of the Fargate cluster is not actually opened
IE, we ran the application on 8080 but it isn't open to the public
TO enable:
- open Security Group for the Service - then navigate to Inbound Rules, Edit them, and add a rule to allow 8080


If you want to run an app on port 80,
- you could run multiple containers, and have one container run Nginx
- Nginx can be used as a Proxy where you change port 8080 to 80






### ECS and Fargate CheatSheet

Elastic Container Service - highly managed container orchestration service - highly secure, reliable nad scalable way to run containers
Components of ECS:
- Cluster - multiple EC2 instances which each house a docker container
- Task Definition - JSON file that defines port and other configs for up to 10 containers that you want to run
- Task - Launches containers that are defined in the Task Defintion - these do not remain running once workload is complete
- Service - ensures tasks reamin running eg web app
- Container Agent - binary on each EC2 instance which monitors, starts and stops tasks

Elastic Container Registry (ECR)
A Fully managed Docker container registry that makes it easy for developers to store, manage and deploy Docker container images
Can be pulled into both ECS and Fargate (ECS with Networking only)

Fargate is Serverless Containers
- Run containers and pay based on duration and consumption
- Creating a Fargate cluster is just like creating a ECS cluster except it is empty (there are no contianers)
- Fargate has Cold Start so if this is an issue, need to use ECS (which does not have Cold Starts)
- No limit on Duration (vs Lambda has a hard limit)
- Pricing: Pay at least one minute and every additional second
- VCPs: this has a lot more computing than you can get with Lambda