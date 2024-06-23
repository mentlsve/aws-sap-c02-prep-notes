# Global Infrastructure

* VPC in one of many AWS regions and then subnets in Availaibility Zones.
* AWS Outposts to extend to on-premises
* AWS Wavelength Zone for single-digit latency to mobile users
* AWS Local Zone for single-digit latency for end users
* CloudFront with regional edge caches and edge locations.

# VPC Basics

* min size /28, max size /16. Size of an existing CIDR block can't be changed
* recommended to use from these ranges: 10/8, 172.16/12, 192.168/16
* first four and last one of a subnet are reserved
* IGW attached to VPC and acts as NAT for instances that have a public IP
* When using EC2 as NAT instance source/destination check must be disabled

# NACL and Security Groups
* NACLs apply at subnet level, Security Group apply at the instance (ENI) level
* NACLs are stateless and can be used to deny traffic
* NACLs are process in order
* NACLs can't block DNS requests to or from the Route 53 Resolver or Instance Metadata Service (IMDS) and few other services
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
