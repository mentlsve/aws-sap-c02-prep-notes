# Containers & Beanstalk

## ECS (Elastic Container Service)

* **Cluster** Logical group of EC2 instances
* **Container instance** EC2 instance running the ECS agent
* **Task definition** Blueprint for a task
* **Task** Running container
* **Service**

## Launch types 

### EC2

* Customer provisions and manages EC2 instances
* Charged per EC2 instance
* Docker volumes (can be EBS), EFS, FSx for Windows File Server

### Fargate

* No Container instances. Fargate provisions and manages compute
* EFS integration


ECS Task role vs ECS role

### Container awareness

Dynamic host port is allocated. Application Load Balancer is aware and forwards to the host port.


## EKS

EKS supports load-balancing with ALB, NLB, CLB

### Auto Scaling

* Vertical Pod Autoscaler: adjusts CPU and memory reservations for pods
* Horizontal Pod Autoscaler: adjusts number of pods in a deployment, replica set, ..
* Workload Auto Scaling
  * Kubernetes Cluster Autoscaler (uses AWS scaling gorups )
  * Karpenter open source autoscaling project (uses Amazon EC2 fleet)

### Load balancing

* Install AWS Load Balancer Controller in cluster. Controller will create
  * ALB when creating a Kubernetes Ingress
  * NLB when creating a Kubernetes service of type LoadBalancer


## Beanstalk

* Everything within the EB environment is launched and managed by EB
* Can use EC2 and ECS for compute
* Environment types
  * **Web servers** process HTTP requests
  * **Workers** process events/messages from SQS

### Deployment Policies

* **All at once**
* **Rolling**: Update a batch of instances, move on if last updated batch is healty
* **Rolling with additional batch** Launch new instance in a batch, move on if last updated batch is healty
* **Immutable** New instances in new ASG and then swap
* *Blue/green* With Route 53