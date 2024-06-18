# VPC Basics

* min size /28, max size /16
* first four and last one of a subnet are reserved
* IGW attached to VPC and acts as NAT for instances that have a public IP.
* When using EC2 as NAT instance source/destination check must be disabled.

NACL and Security Groups
* NACLs are stateless and can be used to deny traffic
* Security groups are stateful and can be used to allow traffic (implicit deny)

# VPC Peering

* No overlapping CIDR allowed
* VPC Peering is not transitive
* VPC Peering requires update of route tables
* VPC Peering can work inter-region and cross-account

# Transit Gateway

* Regional service
* Supports IP Multicast

# VPC Flow Logs

* VPC, Subnet or ENI level
* Can be sent to S3, CloudWach Logs and Kineses Data Firehose.
