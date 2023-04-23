
# Infrastructure

- Region
- Availability Zone
- Edge Location

Services and features are usually scoped by Region of Availability Zone with some being Global.

Regions are made of 3-6 availability zones which are connected with high performance netowrks for high availability of their services.

Regions to use can be chosen based on
- compliance
- proximity
- services available
- cost of services

Availability Zones are made up of one of more datacenters.

Edge Locations are uset to help deliver low latency content in extra locations.


# Access

AWS access is managed through the [[IAM]] service.

Interact with AWS via:

- Management console
- Command Line Interface
- Software Development Kit
- [[HTTP]] Requests

Management console can be logged into using username and password.

CLI, SDK, or Requests use management keys which must be created through the console.


# Services

## Access
- [[IAM]]
- [[Cognito]]

## Networking
- [[Route 53]]
- [[ELB]]
- [[CloudFront]]
- [[AWS API Gateway]]

## Compute
- [[EC2]]
- [[Lambda]]
- [[Step Function]]
- [[SQS]]
- [[SNS]]
- [[Amazon MQ]]

## Storage
- [[EC2 Instance Store]]
- [[EBS]]
- [[EFS]]
- [[S3]]
- [[FSx]]

#### Database
- [[RDS]]
- [[Aurora]]
- [[ElastiCache]]
- [[DynamoDB]]
- [[Document DB]]
- [[Neptune]]
- [[Keyspaces]]
- [[Timestream]]

#### Other
- [[AWS Snow]]
- [[Storage Gateway]]
- [[AWS Transfer Family]]
- [[AWS DataSync]]

## Containers
- [[ECS]]
- [[ECR]]
- [[EKS]]

## Serverless
- [[Lambda]]
- [[DynamoDB]]
- [[AWS API Gateway]]
- [[Step Function]]
- [[Cognito]]

## Data & Analytics
- [[Athena]]
- [[Redshift]]
- [[Open Search]]
- [[EMR]]
- [[Quick Sight]]
- [[Glue]]
- [[Lake Formation]]
- [[Kinesis Streams]]
- [[MSK]]
- [[Kinesis Firehouse]]
- [[Kinesis Data Analytics]]
- [[Kinesis Data Analytics for Apache Flink]]

## Machine Learning
- [[Amazon Rekognition]]
- [[Amazon Transcribe]]
- [[Amazon Polly]]
- [[Amazon Translate]]
- [[Amazon Connect]]
- [[Amazon Lex]]
- [[Amazon Comprehend]]
- [[Amazon SageMaker]]
- [[Amazon Forecast]]
- [[Amazon Kendra]]
- [[Amazon Personalize]]
- [[Amazon Textract]]

## Devops
- [[Elastic Beanstalk]]
