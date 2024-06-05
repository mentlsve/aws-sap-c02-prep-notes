# Amazon Redshift

Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. There are two offerings: Amazon Redshift Serverless and Amazon Redshift provisioned clusters

### Amazon Redshift Provisioned
* Leader nodes and compute nodes
* Node types: DC2 (dense-compute) and RA3
* By default single-AZ, but multi-AZ can be configured for RA3 clusters

Snapshots are point-in-time backups of a cluster. There are two types of snapshots: automated and manual. Amazon Redshift stores these snapshots internally in Amazon S3 by using an encrypted Secure Sockets Layer (SSL) connection.

Amazon Redshift automatically takes incremental snapshots that track changes to the cluster since the previous automated snapshot. Automated snapshots retain all of the data required to restore a cluster from a snapshot.
By default Amazon Redshift takes a snapshot about every eight hours or following every 5 GB per node of data changes, or whichever comes first.
Automated snapshots are deleted at the end of a retention period. The default retention period is one day (but can be configured up to 35 days)

You can configure Amazon Redshift to automatically copy snapshots (automated or manual) for a cluster to another AWS Region. When a snapshot is created in the cluster's primary AWS Region, it's copied to a secondary AWS Region.

### Amazon Redshift Serverless

There are two types of backups in Amazon Redshift Serverless: snapshots that are manually created and recovery points that Amazon Redshift Serverless creates automatically. 

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
