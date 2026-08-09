---
title: "Cấu hình chung AWS Lambda"
weight: 1
chapter: false
pre: "<b>5.4.5.1. </b>"
---

# CẤU HÌNH CHUNG AWS LAMBDA

AWS Lambda được sử dụng làm lớp xử lý nghiệp vụ của backend trong hệ thống Document Chatbot.

Tùy theo chức năng, mỗi Lambda sẽ được cấp IAM Role, Environment Variables và cấu hình mạng phù hợp để truy cập Amazon RDS, Amazon DynamoDB, Amazon Bedrock hoặc Amazon Cognito.

## Kiến trúc cấu hình Lambda

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

Các Lambda trong hệ thống được cấu hình tùy theo dịch vụ mà function cần truy cập.

| Nhóm Lambda | Cấu hình chính |
| --- | --- |
| Lambda RDS | VPC, Security Group, Secrets Manager, `pg8000` |
| Lambda Vector | Amazon Bedrock, `bedrock:InvokeModel` |
| Lambda RAG | Bedrock, DynamoDB, Lambda Invoke |
| Lambda Chat History | DynamoDB |
| Lambda User | Cognito Trigger, DynamoDB |

---

## Cấu hình IAM Role

Mở:

```text
AWS Lambda
→ Function
→ Configuration
→ Permissions
```
Tất cả Lambda cần quyền ghi log:

AWSLambdaBasicExecutionRole

Lambda kết nối Amazon RDS cần thêm:

AWSLambdaVPCAccessExecutionRole
secretsmanager:GetSecretValue

Lambda sử dụng DynamoDB cần các quyền tương ứng:

dynamodb:PutItem
dynamodb:GetItem
dynamodb:Query
dynamodb:UpdateItem
dynamodb:DeleteItem

Lambda sử dụng Amazon Bedrock cần:

bedrock:InvokeModel

Lambda gọi một Lambda khác cần:

lambda:InvokeFunction

## Cấu hình Environment Variables

Mở:

Configuration
→ Environment variables
→ Edit

Một số biến được sử dụng:

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

## Cấu hình VPC

Các Lambda kết nối trực tiếp Amazon RDS cần được đặt trong VPC:

rds-init-dev
rds-vector-insert-dev
rds-vector-search-dev

Mở:

Configuration
→ VPC
→ Edit

Chọn:

VPC:
document-chatbot-vpc-dev

Private Subnets:
document-chatbot-private-a
document-chatbot-private-b

Security Group:
document-chatbot-lambda-rds-sg

Luồng kết nối:

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
