# Installation

1. Run ```winget install -e --id Python.Python.3``` 
2. Install pip  ```py -m ensurepip --upgrade```
3. Install Docker ```winget install -e --id Docker.DockerDesktop```
4. Go to -> "start" and type "Manage App Execution Aliases". Go to it and turn off "Python"
5. Install [LocalStack Cockpit](https://docs.localstack.cloud/get-started/cockpit/)
7. Install aws-cli ```winget install -e --id Amazon.AWSCLI```
8. Browse ```http://localhost:4566/``` to test the setup

# LocalStack
- [AWS Service Feature Coverage](https://docs.localstack.cloud/aws/feature-coverage/)
- [Configuration](https://docs.localstack.cloud/localstack/configuration/)

# Test Commands

- ```aws --endpoint-url=http://localhost:4566 sqs create-queue --queue-name sample-queue2```
- ```aws --endpoint-url=http://localhost:4566 kms --region ap-southeast-2 create-key --tags TagKey=Purpose,TagValue=Test --description "Development test key"```
- ```aws --endpoint-url=http://localhost:4566 kms encrypt --region ap-southeast-2 --key-id 1cc95196-acb1-4279-9063-a3daa3d9a20d --plaintext fileb://C:\TEMP\connectionstring.txt```

# Environment Variables

- AWS_DEFAULT_REGION=ap-southeast-2
- SERVICES=s3,sns,kms,sqs,lambda,dynamodb

Reference: https://docs.localstack.cloud/localstack/configuration/

# AWS Client

- [AWS CLI Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)
- [dynamodb](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/dynamodb/index.html)

# DynamoDB

- [Core Components of Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html)
- [NoSQL Workbench](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.settingup.html)
- [Supported Data Types](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/MidLevelAPILimitations.SupportedTypes.html)
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithItems.html

```aws --endpoint-url=http://localhost:4566 dynamodb list-tables```
```aws --endpoint-url=http://localhost:4566 dynamodb create-table --table-name DEV_Settings_TEMP22 --attribute-definitions AttributeName=InstanceId,AttributeType=S AttributeName=SettingA,AttributeType=N --key-schema AttributeName=InstanceId,KeyType=HASH AttributeName=SettingA,KeyType=RANGE --billing-mode PAY_PER_REQUEST```

