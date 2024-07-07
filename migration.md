# Migration

## AWS Application Discovery Service

* Can collected hostnames, IP addresses, resource allocation (CPU, RAM, Disk I/O)
* Agentless discovery for VWware vCenter (Discovery Connector)
* Discovery agent for pyhsical, VMWare

## AWS Application Migration Service

* Agent-based replication supports continuous data protection
* Creates launch templates
* Short cutover windows measured in minutes
* Highly automated shift-and-lift (rehosting)

## AWS Database Migration Service

* Use Cases: Cloud to cloud, On-premises to cloud, Homogeneous migrations, Hetereogeneous migration, continuous data replication
* SCT = Schema Conversion Tool for heterogeneous migration
* Sources
* Destinations

## AWS Migration Hub

## AWS DataSync

DataSync can copy data between Network File System (NFS) shares, Server Message Block (SMB) shares, Hadoop Distributed File Systems (HDFS), self-managed object storage, AWS Snowcone, Amazon Simple Storage Service (Amazon S3) buckets, Amazon Elastic File System (Amazon EFS) file systems, Amazon FSx for Windows File Server file systems, Amazon FSx for Lustre file systems, Amazon FSz for OpenZFS file systems, and Amazon FSx for NetApp ONTAP file systems.


## Snowball Family

* Snowbmobile 100 PB
* Snowball 80TB or 50TB
* Snowball Edge Compute Optimized (compute capability) 100 TB
* Snowball Edge Storage Optimized (compute capability) 100 TB
* Snowcone (Samll device used for edge computing)

Optimize by:
* Use latest Max or Linux Snowball client
* Batch files together
* Parallelize (same workstation, multiple workstations)
* Copy directories instead of files

## The 7 Rs

* Retire
* Retain
* Relocate (Lift & Shift to VMWare on AWS)
* Rehost (Lift & Shift to EC2)
* Repurchase (Replace with SaaS)
* Replatform (Move from MySQL to RDS)
* Rearchitect (Cloud-native, e.g. serverless)

### Rehost

* Use AWS Application Migration Service

### Replatform

* Use AWS Database Migration Service (with Schema Conversion Tool)
* Use AWS Application Migration Service or code-level migration