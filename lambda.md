# Lambda

## Concurrency

* Concurrent execution of lambda functions is possible up to burst or account limit. Burst concurrency quota in Frankfurt is 1000, in Ireleand is 3000.
* Beyond that `Rate exceeded` and `429 TooManyRequestsException`

## Versions and Aliases

* A qualified ARN has a version suffix, an unqualified ARN does not have a version suffix
* You cannot create an alias from an unqualified ARN

You can point an alias to a maximum of two Lambda function versions. The versions must meet the following criteria:

    * Both versions must have the same execution role.
    * Both versions must have the same dead-letter queue configuration, or no dead-letter queue configuration.
    * Both versions must be published. The alias cannot point to $LATEST.

`aws lambda create-alias --function-name my-function --name alias-name --function-version version-number --description " "`
`aws lambda create-alias --name routing-alias --function-name my-function --function-version 1  --routing-config AdditionalVersionWeights={"2"=0.03}`