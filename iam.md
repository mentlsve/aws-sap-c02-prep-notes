* Identity-based policies can be applied to users, groups and roles
* 5000 IAM users per account
* IAM ROles have a trust policy and a permission policy
* Inlince policies have 1:1 relationship with principal
* Managed policies can be reused and are AWS or customer managed
* `aws:PrincipalTag/<key>` for ABAC
* Permission boundaries are applied to users and roles

## Identity Federation

* SAML 2.0
* Custom Identity Broker
* Web Identity Federation with(out) Cognito

### SAML 2.0

* Supports ADFS or any IDP compatible IdP
* sts:AssumeRoleWithSAML to get temporary credentials 

## Directory Services

### AWS Managed Microsoft AD

* HA pair of DCs in your VPC in two different AZs, number of DCs can be scaled.
* Establish trust to on-premises AD, from on-premises AD or both.
* Trust is no replication / synchronization.
* Can integrate with some AWS services, e.g. RDS for SQL Server, AWS SSO, Amazon WorkSpaces

### AD Connector 

* Kind of a proxy to the on-premises AD
* No caching
* Objects are only defined on-premises
  

### Simple AD

* AD-compatible managed directory
* Can not be joined with on-premises AD
* no MFA
