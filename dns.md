# Route 53

## Private hosted zone 

* associate to VPC
`aws route53 associate-vpc-with-hosted-zone --hosted-zone-id <value> --vpc <value>`
* VPC ENable DNS Hostnames, Enable DNS Resolution
`aws ec2 modify-vpc-attribute --enable-dns-hostnames` for instances in the vpc
`aws ec2 modify-vpc-attribute --enable-dns-support` for DNS queries from within the VPC

* Associate a VPC ins account_a with hosted zone in account_b. account_b created the hosted zone.
    ```
    In Account B: aws ec2 create-vpc-association-authorization --hosted-zone-id <value> -vpc VPCRegion=string,VPCId=string

    In Account A: aws route53 associate-vpc-with-hosted-zone --hosted-zone-id <value> --vpc <value>
    ```


## Routing policies

|||
|---|---|
|Simple||
|Failover|Negative halth check for primary -> respond with secondary|
|Geolocation|Response based on the geographic location of your users, meaning the location that DNS queries originate from. For private hosted zones, Route 53 responds to DNS queries based on the AWS Region of the VPC that the query originated from|
|Geoproximity||
|Latency||
|Multivalue||
|Weighted||

https://disaster-recovery.workshop.aws/en/services/networking/route53/routing-policies.html#:~:text=Geolocation%20routing%20policy%20%E2%80%94%20Use%20when,one%20location%20to%20resources%20elsewhere.

## Route 53 Resolver

* Resources in VPC ask Route 53 and Route 53 forwards to the outbound ressolver
* On-premieses asks the inbound resolver which forwards to Route 53

## Route 53 Health Checks

Health checks can monitor

* an endpoint
    * HTTP and HTTPS health checks: Healthy if tcp established within 4 seconds and 2xx/3xx response within 2 seconds
    * HTTP and HTTPS health checks with string matching: above +  the string must appear entirely in the first 5,120 bytes of the response body
    * TCP health checks: ealthy if tcp established within 10 seconds
* other health checks
* CloudWatch alarms