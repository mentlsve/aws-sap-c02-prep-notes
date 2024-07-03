# Placemenet groups

* Cluster: Placed in the same high-bisection bandwidth segment of the network. Single AZ.
* Partition:  Amazon EC2 ensures that each partition within a placement group has its own set of racks. Each rack has its own network and power source. Up to 7 partitions per AZ.
* Spread: A rack level spread placement group can span multiple Availability Zones in the same Region. In a Region, a rack level spread placement group can have a maximum of seven running instances per Availability Zone per group

# ENI, EFA, ENA

* The Elastic Network Adapter (ENA) supports network speeds of up to 100 Gbps for supported instance types.
* The Intel 82599 Virtual Function interface supports network speeds of up to 10 Gbps for supported instance types.
* The OS-bypass capabilities of EFAs are not supported on Windows instances. If you attach an EFA to a Windows instance, the instance functions as an Elastic Network Adapter, without the added EFA capabilities.
* ENIs can be remapped in same AZ, EIP can be remapped across AZs

# ASG

* Available metrics for target tracking
    * ASGAverageCPUUtilization
    * ASGAverageNetworkIn (bytes received on all network interfaces in ASG)
    * ASGAverageNetworkOut
    * ALBRequestCountPerTarget (requests completed per target)
* Dynamic Scaling 
    * Simple Scaling
    * Step Scaling (can consider size of the alarm breach)
    * Scheduled Scaling
* Termination Policy (choose AZ with most instances, choose with oldest config, choose closes to next billing hour)
* Cooldowns - wait until effect of previous activity is visible
* Lifecycle: Pending -> Pending:Wait (Hook) -> Pending:Proceed (Hook) -> InService -> Terminating -> Terminating:Wait (Hook) -> Terminating:Proceed (Hook) -> Terminated
* Launch Template: AMI + Instance type + ...


# ELB

* Application Load Balancer: Layer 7 routing (host, path, paramemeter, query) supports IP addresses, Lambda functions and containers
* Network Load Balancer: Layer 4 routing (IP, port). Can attach a static / ealstic IP
* Classic Load Balancer: Old generation
* Gateway Load Balancer: Layer 3 (all packets on all ports)
* Application sees the IP of the load balancer if the ELB is an ALB or if it is an NLB AND the instance was specified by IP and traffic is TCP/TLS
* Application sees the IP of the client if the ELB is a NLB and the instance was specified by instance ID OR traffic is UDP / TCP_UDP
* Network Load Balancers can preserve the source IP address of clients when routing requests to backend targets. When you disable client IP preservation, the source IP address is the private IP address of the Network Load Balancer. By default, client IP preservation is enabled (and can't be disabled) for instance and IP type target groups with UDP and TCP_UDP protocols.
* Client IP Preservation, defaults
    * Instance type target groups: Enabled
    * IP type target groups (UDP, TCP_UDP): Enabled (can't be disabled)
    * IP type target groups (TCP, TLS): Disabled

# EBS

* EC2 Instance can have multiple volumes attached
* 1 Volume can be attached to up to 16 EC2 Instances with EBS multi-attach (Provisioned IOPS io1, Nitro-based, single AZ)
* EBS volumes are replicated within an AZ
* EBS volumens and EC2 instances must be in same AZ

gp2, gp3, io1, io2 

||gp3|gp2|io2(Block Express)|io1
|---|---|---|---|---|
|Size|1 GiB - 16 TiB|1 GiB - 16 TiB|4 GiB - 64 TiB|4 GiB - 16 TiB|
|IOPS|3,000 - 16,000|100 - 16,000|256,000|64,000|
|Max IOPS| Maximum IOPS can be provisioned for volumes 32 GiB or larger | IOPS performance scales linearly between a minimum of 100 and a maximum of 16,000 at a rate of 3 IOPS per GiB of volume size. 
|Max throughput per volume|1,000 MiB/s|250 MiB/s|4,000 MiB/s|1,000 MiB/s|
|Amazon EBS Multi-attach|No|No|Yes|Yes|
|Boot volume|Yes|Yes|Yes|Yes|

* Snapshots are regional, because they are actually stored in S3
* Rebooting an EC2 Instance with Instance store will preserve data, stopping will not preserve data