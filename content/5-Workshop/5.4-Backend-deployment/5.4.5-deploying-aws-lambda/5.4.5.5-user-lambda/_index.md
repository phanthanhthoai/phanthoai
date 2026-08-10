---
title: "User Lambda"
weight: 5
chapter: false
pre: "<b>5.4.5.5. </b>"
---


# USER SYNCHRONIZATION LAMBDA

The `user-post-confirmation-dev` Lambda function is used to synchronize user information from Amazon Cognito to Amazon DynamoDB.

The Lambda is configured as the **Post Confirmation Trigger** for the Cognito User Pool.

## Processing Flow

{{< mermaid >}}
graph LR;
    USER[Câu hỏi người dùng] --> RAG[ChatbotRAG-dev];
    RAG --> TITAN[Amazon Titan Embeddings];
    TITAN --> SEARCH[rds-vector-search-dev];
    SEARCH --> RDS[Amazon RDS PostgreSQL];
    RDS --> CHUNKS[Top K Chunks];
    CHUNKS --> RAG;
    RAG --> NOVA[Amazon Nova Lite];
    NOVA --> ANSWER[Câu trả lời];
    ANSWER --> HISTORY[ChatHistory-dev];
{{< /mermaid >}}

---

## Lambda Configuration

Function:

```text
user-post-confirmation-dev

-Environment Variable:

-USERS_TABLE_NAME = Users-dev

-Required Lambda permissions:

dynamodb:UpdateItem

-Required Amazon Cognito permissions:

lambda:InvokeFunction
```
to invoke the Lambda after the user confirms their account.

## Cognito Trigger Configuration

Open the Amazon Cognito User Pool.

1. Select:

Extensions
→ Lambda triggers

2. Under Post Confirmation, select:

user-post-confirmation-dev

3. Then save the configuration.

4. Trigger flow:

User Confirmed
→ Cognito Post Confirmation
→ user-post-confirmation-dev
→ Users-dev

## User Data

The Lambda retrieves attributes from Cognito such as:

sub
email
name

Where:

sub

is used as the user's userId.

Information is stored in:

Users-dev
