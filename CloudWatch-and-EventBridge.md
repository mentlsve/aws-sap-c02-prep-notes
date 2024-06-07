# CloudWatch

## CloudWatch Metrics

## CloudWatch Alarms

## CloudWatch Insights

## CloudWatch Synthetics 

# EventBridge

Each AWS service that generates events sends them to EventBridge as either best effort (in some rare cases an event might might be lost) or durable (at least once) delivery attempts. E.g. AWS Batch sends an event when the status of the job changes, EC2 Auto Scaling sends an event when a scale-out happens, ...

An account includes a *default event bus* that automatically receives events from AWS services.

For own events *custom event buses* can be created and to get events from SaaS providers *partner event buses* can be used (e.g. Adobe or SailPoint)

Amazon EventBridge Pipes is for point-to-point integrations and Amazon EventBridge Event Bus for one-to-many integration.

The default event bus in your AWS account only allows events from one account. You can grant additional permissions to an event bus by attaching a resource-based policy to it. With a resource-based policy, you can allow PutEvents, PutRule, and PutTargets API calls from another account. 

KMS key for EventBridge

## EventBridge Rules
Define rule
* define Event Pattern
* define target, e.g. Lambda, SQS, SNS, API destination. Interesting ones are
  * EBS CreateSnapshot API call
  * EC2 RebootInstances API call
  * EC2 StopInstances API call
  * EC2 TerminateInstances API call
  
https://docs.aws.amazon.com/eventbridge/latest/userguide/eb-targets.html#eb-console-targets

