## EventBridge

EventBridge is a serverless service that uses events to connect application components together, making it easier for you to build scalable event-driven applications.

The default event bus in your AWS account only allows events from one account. You can grant additional permissions to an event bus by attaching a resource-based policy to it. With a resource-based policy, you can allow PutEvents, PutRule, and PutTargets API calls from another account. 

### Concepts

* Every account includes a **default event bus**
* Additional **custom event bus**(es) can be cretead
* **Partner event buses** can be created to receive events from SaaS partners
* A **rule** receives incoming events and sends them as appropriate to targets for processing. Each rule is defined for a specific event bus, and only applies to events on that event bus. A single rule can send an event to up to five targets.
* A **target** can receive multiple events from multiple event buses. Targets can be AWS services (e.g. API Gateway, Lambda function, SQS, SNS, Kineses stream, Firehose delivery, ...),  AWS API calls (RebootInstances, StopInstances, TerminateInstances, CreateSnapshot) amd event bus in same/other account same/other region.

### Service specific configuration / behavior

## SQS

### Service specific configuration / behavior

* To permanently remove a message from the queue, you must explicitly send a delete request after processing the message to confirm successful receipt and handling.

#### Types

**FIFO**

* High throughput: 300 messages per second. Up to 10 messages can be batched per operation ~3000 messages per second
* First-in First-out delivery
* Exactly-once processing

**Standard**

* Unlimited throughput
* Best-effort ordering
* At-least-once delivery

### Configuration

* If the processer does not delete the message within the **visibility timeout** the message becomes visibile again. Should be between 0 seconds to 12 hours.
* Amazon SQS automatically deletes messages that have been in a queue for more than the maximum **message retention period**. Should be between 1 to 14 days.
* **Maximum message size** should be between 1 KB and 256 KB.

#### Encryption

Amazon SQS provides in-transit encryption by default. To add at-rest encryption to your queue, enable server-side encryption.

* Amazon SQS key (SSE-SQS)
* AWS Key Management Service key (SSE-KMS)

#### Access Policy

Define who can send messages to the queue
Define who can receive messages from the queue

#### Dead letter queue

The Maximum receives value determines when a message will be sent to the DLQ. If the ReceiveCount for a message exceeds the maximum receive count for the queue, Amazon SQS moves the message to the associated DLQ (with its original message ID).

## SNS

Publishers communicate asynchronously with subscribers by sending messages to a **topic**, which is a logical access point and communication channel.

### Service specific configuration / behavior

#### Types

**FIFO**
  * Strictly-preserved message ordering
  * Exactly-once message delivery
  * High throughput, up to 300 publishes/second
  * Only SQS as subscriber

**Standard**
  * Best-effort message ordering
  * At-least once message delivery
  * Highest throughput
  * A2P subscribers can be SMS, Mobile push, Email
  * A2A subscribers can be SQS, Lambda, Kineses Data Firehose, HTTPS

#### Message delivery

* **Raw message (no SNS metadata) delivery** can be configured for SQS, Amazon Data Firehose & HTTPS
* Cross-account delivery to SQS in other accounts. In source account create **access policy** which allows `sns:Subscribe` on the topic.
* **Cross-region delivery** can be configured for SQS and Lambda
* **Delivery policy** defines how Amazon SNS retries the delivery of messages when server-side errors occur (when the system that hosts the subscribed endpoint becomes unavailable). There are 4 phases (example values are for Lambda, SQS, Data Firehose)
  * Immediate retry phase: 3 times, without delay
  * Pre-backoff phase: 2 times, 1 second apart
  * Backoff phase: 10 times, with backoff from 1 to 20 seconds
  * Post-backoff phase: 100,000 times, 20 seconds apart

  Maximum then is 100,015 attempts over 23 days

#### Encryption 

SSE encrypts messages as soon as Amazon SNS receives them. The messages are stored in encrypted form, and only decrypted when they are sent.

https://ibkrm.github.io/aws-sa-pro-notes/app-services/sqs/

