# Amazon Redshift

Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. There are two offerings: Amazon Redshift Serverless and Amazon Redshift provisioned clusters

### Amazon Redshift Provisioned
* Leader nodes and compute nodes
* Node types: DC2 (dense-compute) and RA3
* By default single-AZ, but multi-AZ can be configured for RA3 clusters

A backup in Amazon Redshift Serverless is a point-in-time representation of the objects and data in your namespace. 
There are two types of backups: snapshots that are manually created and recovery points that Amazon Redshift Serverless automatically creates for you. 
Recovery points are created every 30 minutes and are kept for 24 hours.

## Redshift Spectrum

Using Amazon Redshift Spectrum, you can efficiently query and retrieve structured and semistructured data from files in Amazon S3 without having to load the data into Amazon Redshift tables.

## Redshift Workload Management
