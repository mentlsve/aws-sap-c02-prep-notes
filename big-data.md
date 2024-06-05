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


# Amazon Document DB

If there is instance failure, Amazon DocumentDB automates failover to one of up to 15 Amazon DocumentDB replicas customers have created in any of three Availability Zones.

* On-demand instances: The amount of compute instances for a cluster (pricing per second with a 10-minute minimum).
* Database I/O: The amount of I/O used when reading and writing data to your cluster’s storage volume (pricing per million I/Os).
* Database storage: The amount of data stored in your cluster's storage volume (pricing per GB/month).
*   Amazon DocumentDB Standard (pay-per-use I/O configuration)
*   Amazon DocumentDB I/O-Optimized (I/O included configuration): You are not charged for Database I/O
* Backup storage: The amount of backup storage used in excess of your cluster’s database storage usage (pricing per GB/month).

## Elastic Clusters

Amazon DocumentDB Elastic Clusters are a new type of Amazon DocumentDB cluster that lets you elastically scale your document database to handle millions of reads and writes with petabytes of storage capacity. Basically the first two pricing components (On-demand instances, Database I/O) get replaced by vCPU: The amount of compute measured in vCPUs for a cluster (priced per minute with a 10-minute minimum).

## Global Clusters

Amazon DocumentDB Global Clusters is an optional feature that provides fast replication across regions with latencies of less than one second using dedicated infrastructure with little to no impact to your workload’s performance. With global clusters, you can recover from region-wide outages and serve low-latency global reads by allowing reads from the nearest DocumentDB cluster.
