# Site to Site VPN

* Virtual Private Gateway is attached to VPC and represents the endpoint on AWS
* Customer Gateway is the representation of the other (e.g. on-premises) endpoint
* Supports static routing and dynamic routing (BGP)
* BGP requires configuration of ASN of CGW and ASN on VGW

## Transitive traffic

* You can not use a NAT Gateway to reach the Internet from on-premises -> CGW -> VGW -> NAT Gateway -> IGW -> Internet. Must use a NAT Instance instead.

From [docs](https://docs.aws.amazon.com/vpc/latest/userguide/vpc-nat-gateway.html):
> You can't route traffic to a NAT gateway through a VPC peering connection.

> You can't route traffic through a NAT Gateway when traffic arrives over a hybrid connection (Site to Site VPN or Direct Connect) through a Virtual Private Gateway.

> You can route traffic through a NAT Gateway when traffic arrives over a hybrid connection (Site to Site VPN or Direct Connect) through a transit gateway.

# AWS VPN CloudHub

* Connect up to 10 Customer Gateways for each VGW
* Can be used for failover, in case connectivity between on-premises data centers fails

# AWS Client VPN

* Uses OpenVPN
* Client VPN is compatible with VPC peering

## Client CIDR range

* The address range cannot overlap with the target network address range, the VPC address range or any of the routes that will be associated with the Client VPN endpoint. The client address range must be at minimum /22 and not greater than /12 CIDR block size. You cannot change the client address range after you create the Client VPN endpoint.
  
## Target Network
* A target network is a subnet in a VPC. A Client VPN endpoint must have at least one target network to enable clients to connect to it and establish a VPN connection.
* The subnet's CIDR block cannot overlap with the client CIDR range of the Client VPN endpoint.
* If you associate more than one subnet with a Client VPN endpoint, each subnet must be in a different Availability Zone. We recommend that you associate at least two subnets to provide Availability Zone redundancy

# Direct Connect

* Dedicated connection or hosted connection (allows to add/remove capacity on demand)
* 1 month lead time
* Data in transit is not encryped but private
* Not redundant by default
* Direct Connect has multiple Virtual Interfaces (VIF)
  * Public: Connect to public AWS endpoints
  * Private: Connect to resources in your VPC, including VPC Interface endpoints
  * Transit: Connect to resources in a VPC via Transit Gateway
* Link Aggregation Groups: Sum up up to 4 dedicated connections with same bandwith terminating at the same Direct connect endpoint into a logical one.

## Direct Connect Gateway

* One ore more VPC in many different regions
* To connect to a Transit Gatway a Direct Connect Gateway is required
* Site Link allows direct connection between connected data centers
