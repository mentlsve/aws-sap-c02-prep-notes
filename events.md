# SQS

* To permanently remove a message from the queue, you must explicitly send a delete request after processing the message to confirm successful receipt and handling.



## Standard

* Unlimited throughput
* Best-effort ordering
* At-least-once delivery

## FIFO

* High throughput: 300 messages per second. Up to 10 messages can be batched per operation ~3000 messages per second
* First-in First-out delivery
* Exactly-once processing