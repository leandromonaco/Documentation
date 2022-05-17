# AWS CDK

[AWS Cloud Development Kit](https://aws.amazon.com/cdk/)
[Getting started with the AWS CDK](https://docs.aws.amazon.com/cdk/v2/guide/getting_started.html)

1. ```npm install -g aws-cdk``` 
2. ```cdk --version``` 


* `dotnet build src` compile this app
* `cdk deploy`       deploy this stack to your default AWS account/region
* `cdk diff`         compare deployed stack with current state
* `cdk synth`        emits the synthesized CloudFormation template

# SAM

- [AWS Serverless Application Model](https://aws.amazon.com/serverless/sam/)
- ```winget install -e --id Amazon.SAM-CLI```
- ```sam --version```

# LocalStack 
## Installation

1. Run ```winget install -e --id Python.Python.3``` 
2. Install pip  ```py -m ensurepip --upgrade```
3. Install Docker ```winget install -e --id Docker.DockerDesktop```
4. Go to -> "start" and type "Manage App Execution Aliases". Go to it and turn off "Python"
5. Install [LocalStack Cockpit](https://docs.localstack.cloud/get-started/cockpit/)
7. Install aws-cli ```winget install -e --id Amazon.AWSCLI```
8. Browse ```http://localhost:4566/``` and ```http://localhost:4566/health``` to test the setup

## Reference
- [AWS Service Feature Coverage](https://docs.localstack.cloud/aws/feature-coverage/)
- [Configuration](https://docs.localstack.cloud/localstack/configuration/)

## Test Commands

- ```aws --endpoint-url=http://localhost:4566 sqs create-queue --queue-name sample-queue2```
- ```aws --endpoint-url=http://localhost:4566 kms --region ap-southeast-2 create-key --tags TagKey=Purpose,TagValue=Test --description "Development test key"```
- ```aws --endpoint-url=http://localhost:4566 kms encrypt --region ap-southeast-2 --key-id 1cc95196-acb1-4279-9063-a3daa3d9a20d --plaintext fileb://C:\TEMP\connectionstring.txt```

## Environment Variables

- AWS_DEFAULT_REGION=ap-southeast-2
- SERVICES=s3,sns,kms,sqs,lambda,dynamodb
- DYNAMODB_SHARE_DB=1
- PERSIST_ALL=1
- USE_SINGLE_REGION=true


# AWS Client

- [AWS CLI Command Reference](https://awscli.amazonaws.com/v2/documentation/api/latest/index.html)
- [dynamodb](https://awscli.amazonaws.com/v2/documentation/api/latest/reference/dynamodb/index.html)

# DynamoDB

- [Core Components of Amazon DynamoDB](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.CoreComponents.html)

- [Supported Data Types](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/MidLevelAPILimitations.SupportedTypes.html)
- https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/WorkingWithItems.html

```aws --endpoint-url=http://localhost:4566 dynamodb list-tables```
```aws --endpoint-url=http://localhost:4566 dynamodb create-table --table-name DEV_Settings_TEMP22 --attribute-definitions AttributeName=InstanceId,AttributeType=S AttributeName=SettingA,AttributeType=N --key-schema AttributeName=InstanceId,KeyType=HASH AttributeName=SettingA,KeyType=RANGE --billing-mode PAY_PER_REQUEST```

## NoSQL Workbench
- [NoSQL Workbench](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/workbench.settingup.html)

1. Open NoSQL Workbench
2. Add Connection
3. Click "DynamoDB Local"
4. Hostname: localhost | Port: 4566

# Lambda Functions

- https://docs.aws.amazon.com/lambda/latest/dg/lambda-csharp.html
- https://aws.amazon.com/blogs/developer/net-core-global-tools-for-aws/
- ```dotnet new lambda.EmptyFunction --help```

Create Lambda Function
- Install DotNet Lambda templates ```dotnet new -i Amazon.Lambda.Templates```
- Run ```dotnet new lambda.EmptyFunction --name AwsLambdaFunction```
- ```dotnet build```
- ```dotnet publish -c Release -o publish p:PublishReadyToRun=false```
- zip content of the .\publish\ folder (function.zip)

Package Function
cdk init app --language=csharp
configure deployment settings
cdk synth

Test Locally
sam local invoke -t .\cdk.out\AwsLambdaStack.template.json





- ```aws --endpoint-url=http://localhost:4566 iam create-role --role-name lambda-dotnet-ex --assume-role-policy-document '{"Version": "2012-10-17", "Statement": [{ "Effect": "Allow", "Principal": {"Service": "lambda.amazonaws.com"}, "Action": "sts:AssumeRole"}]}'```
- ```aws --endpoint-url=http://localhost:4566 iam attach-role-policy --role-name lambda-dotnet-ex --policy-arn arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole```
- ```aws --endpoint-url=http://localhost:4566 lambda create-function --function-name lambda-dotnet-function --zip-file fileb://function.zip --handler Sample.Lambda.DotNet::Sample.Lambda.DotNet.Function::FunctionHandler --runtime dotnet6 --role arn:aws:iam::000000000000:role/lambda-dotnet-ex```
- ```aws --endpoint-url=http://localhost:4566 lambda list-functions```
- ```aws --endpoint-url=http://localhost:4566 lambda delete-function --function-name lambda-dotnet-function```
- ```aws --endpoint-url=http://localhost:4566 lambda invoke --function-name lambda-dotnet-function --payload "\"Just Checking If Everything is OK again\"" --cli-binary-format raw-in-base64-out response.json --log-type Tail```



