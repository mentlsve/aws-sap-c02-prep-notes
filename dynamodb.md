## DynamoDB

DynamoDB is a fully managed, key-value, and document database that delivers single-digit-millisecond performance at any scale. 

* Tables with items having attributes
* Items can have a TTL
* Primary key = partition key + sort key (optional)

Table classes:
* Dynamo DB Standard: Throughput (read and write) as the dominant table cost
* Dynamo DB Standard-IA: Storage as the dominant table cost

Read/write capacity settings:
* Provisionend (auto-scaling can be enabled for RCU/WCU individually)
  * 1 RCU: One strongly consistent read operation or two eventually consistent read operations per second for an item up to 4 KB 
  * 1 WCU: One write per second for an item up to 1 KB.
* On-demand (can set maximum)

Encryption at rest:
* AWS KMS key owned and managed by DynamoDB. No fees
* AWS managed key `aws/dynamodb` stored in accoun. AWS KMS charges apply
* Customer managed key (from same/other account). AWS KMS charges apply

Recovery & Backup:
* PITR: Amazon DynamoDB point-in-time recovery (PITR) provides automatic continuous backups of your DynamoDB table data. Point-in-time recovery (PITR) backups are fully managed by DynamoDB and provide up to 35 days of recovery points at a per second granularity. 
* On-demand backups

## Streams

* DynamoDB offers two streaming models for change data capture: Kinesis Data Streams for DynamoDB and DynamoDB Streams.
https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/streamsmain.html