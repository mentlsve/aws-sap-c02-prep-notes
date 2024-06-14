# DMS

* Managed migration and replication service
* Can be used for homogeneous and heterogeneous migrations. It is especially beneficial for heterogeneous migrations, since the vendor provided tools (e.g. mysqldump) can be more performant and cheaper. AWS DMS wins when flexibility is required and downtime needs to be minimal. With AWS DMS the source DB remains operational.
* DMS specializes on data migration, for schema migration AWS SCT (Schema Conversion Tool) should be used.
* Typical use cases: moving to managed databases, eliminating licensing costs and accelerating business growth, improving integration with data stores, and replicating changes to other data stores.

## Architecture

* An AWS DMS replication instance is basically an EC2 instance and it sits in a VPC.
  * Multi-AZ: primary replication instance in one AZ, standby in another AZ. 
* The AWS DMS replication instance connects to the source and target DB. For these endpoints required information includes engine type, server name, port, credentials.
* There are three options for migration type in a an AWS Database Migration Task Full Load, Full Load + CDC, CDC Only
* Instances which should be considered: T2/T3 for test, C4 for heterogeneous, R4/R5 for many transactions
