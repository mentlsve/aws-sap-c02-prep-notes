# Datbases

## RDS

Supported engines: Db2, MariaDB, Microsoft SQL Server, MySQL, Oracle, PostgreSQL
* When lambda needs to access DB, lambda must be deployed to VPC
* Oracle: RDS for Oracle does not support RAC, if you want RAC deploy Oracle on EC2

### Backups
* Automated backup creates a snapshot with retention of 0-35 days.
* Oracle: Use RDS Backups to backup and restore from RDS to RDS. Use Oracle RMAN to restore from RDS to non-RDS

### Snapshots
* Manual backups: Snapshots do not expire
* Maintenance windows

### Security features

* Security groups
* Enable TLS
* KMS encryption
* Enable encryption at rest, must be enabled at creation time, can't be enabled/disabled afterwards
* You can't restore an unecrypted backup/snapshot to an encrypted instance. Workaround is to copy the snapshot and encrypt it during copy.
* Transparent data encryption for Oracle and SQL server
* IAM database authentication wirks with MariaDB, MySQL, PostgreSQL

### Multi-AZ

* Automated backups are taken from standby, with exception of SQL Server where it is taken from primary
* Always span two AZs in a single region
* One DNS name. Automatic failover from primary to standby.
* Multi-AZ creates a passive standby. There is synchronous replication from the master to the standby. Multi-AZ is for disaster recovery not for scaling.


### Read replica

* No backups configured by default
* Same AZ, other AZ - same region, other region
* Manual promotion to standalone instance
* Read replica for scaling. There is asynchronous replication from the master to the read replicas
* Use Route53 and weighted record set for distributing across read replicas (+health check)
* When you promote a read replica, RDS reboots the DB instance before making it available. The promotion process can take several minutes or longer to complete, depending on the size of the read replica.

## Aurora

* PostgreSQL and MySQL compatible
* Storage grows automatically up to 128 TB
* 6 copies of data across 3AZ, 4 copies out of 6 needed for writes, 3 copies out of 6 needed for reads
* multi-AZ
* up to 15 RR
* Croos-region replication for RR.
* Aurora PostgreSQL doesn't support cross-Region Aurora Replicas. 
* You can create an Aurora read replica of an Aurora MySQL DB cluster in a different AWS Region, by using MySQL binary log (binlog) replication. Each cluster can have up to five read replicas created this way, each in a different Region.
* Reader endpoint (load-balancing), Writer endpoint, Custom endpoint, Instance endpoint

### Aurora Serverless


### Aurora Global Database

* 1 primary region (read-write)
* up to 5 secondary region (read-only), replication lag less than 1 second
* up to 16 RR per secondary region
* Write Forwarding: secondary clusters forward writes to primary cluster


## Convert RDS to Aurora

* RDS DB Instance --(snapshot)--> Snapshot --(restore)--> Aurora DB Instance
* RDS DB Instance --(new read replica)--> Aurora Read Replica --(promote)--> Aurora DB Instance