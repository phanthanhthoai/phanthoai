---
title: "AWS Lambda General Configuration"
date: 2026-08-09
weight: 1
chapter: false
pre: "<b>5.4.5.1. </b>"
---

# AWS LAMBDA GENERAL CONFIGURATION

AWS Lambda serves as the backend business logic layer within the Document Chatbot system.

Depending on its specific function, each Lambda is assigned an appropriate IAM Role, Environment Variables, and network configuration to access Amazon RDS, Amazon DynamoDB, Amazon Bedrock, or Amazon Cognito.

## Lambda Configuration Architecture

{{< mermaid >}}
flowchart LR
L[AWS Lambda]

L --> IAM[IAM Role]
L --> ENV[Environment Variables]
L --> VPC[VPC]
L --> LOG[CloudWatch Logs]

VPC --> RDS[(Amazon RDS)]
L --> DDB[(Amazon DynamoDB)]
L --> BR[Amazon Bedrock]
L --> COG[Amazon Cognito]
{{< /mermaid >}}

The Lambdas in the system are configured based on the services the function needs to access.

| Lambda Group | Key Configuration |
| --- | --- |
| Lambda RDS | VPC, Security Group, Secrets Manager, `pg8000` |
| Lambda Vector | Amazon Bedrock, `bedrock:InvokeModel` |
| Lambda RAG | Bedrock, DynamoDB, Lambda Invoke |
| Lambda Chat History | DynamoDB |
| Lambda User | Cognito Trigger, DynamoDB | ---

## IAM Role Configuration

Navigate to:

```text
AWS Lambda
→ Function
→ Configuration
→ Permissions
```
All Lambda functions require logging permissions:

AWSLambdaBasicExecutionRole

Lambda functions connecting to Amazon RDS require:

AWSLambdaVPCAccessExecutionRole
secretsmanager:GetSecretValue

Lambda functions using DynamoDB require the corresponding permissions:

dynamodb:PutItem
dynamodb:GetItem
dynamodb:Query
dynamodb:UpdateItem
dynamodb:DeleteItem

Lambda functions using Amazon Bedrock require:

bedrock:InvokeModel

Lambda functions invoking another Lambda function require:

lambda:InvokeFunction

## Environment Variables Configuration

Navigate to:

Configuration
→ Environment variables
→ Edit

Variables used:

### Amazon RDS
DB_HOST = chatbot-postgres-dev.cfqau4o0ohw4.ap-southeast-1.rds.amazonaws.com
DB_PORT = 5432
DB_NAME = chatbot_db
DB_SECRET_ARN = arn:aws:secretsmanager:ap-southeast-1:043272859712:secret:rds!db-cd60cc96-ec83-4b76-9aca-b2a4bf965734-mFRW5l

### Amazon DynamoDB
CHAT_TABLE_NAME = ChatHistory-dev
USERS_TABLE_NAME = Users-dev

### Amazon Bedrock
BEDROCK_REGION = us-east-1
EMBEDDING_MODEL_ID = amazon.titan-embed-text-v2:0
CHAT_MODEL_ID =

## VPC Configuration

Lambda functions connecting directly to Amazon RDS must be placed within the VPC:

rds-init-dev
rds-vector-insert-dev
rds-vector-search-dev

Navigate to:

Configuration
→ VPC
→ Edit

Select:

VPC:
document-chatbot-vpc-dev

Private Subnets:
document-chatbot-private-a
document-chatbot-private-b

Security Group:
document-chatbot-lambda-rds-sg

Connection flow:

{{< mermaid >}}
flowchart LR
L[AWS Lambda]
SG1[Lambda Security Group]
SG2[RDS Security Group]
R[(RDS PostgreSQL)]

L --> SG1
SG1 -->|TCP 5432| SG2
SG2 --> R

{{< /mermaid >}}
