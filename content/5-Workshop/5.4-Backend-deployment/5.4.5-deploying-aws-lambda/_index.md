---
title: "Deploying AWS Lambda"
weight: 5
chapter: false
pre: "<b>5.4.5. </b>"
---

# DEPLOYING AWS LAMBDA

AWS Lambda serves as the primary backend business logic layer for the Document Chatbot system.

Instead of deploying a continuously running backend server, the system breaks down functionality into multiple independent Lambda functions. Each function handles a specific task, such as:

- Initializing the PostgreSQL database.
- Writing vector embeddings to Amazon RDS.
- Generating vector embeddings using Amazon Bedrock.
- Performing vector searches in PostgreSQL using `pgvector`.
- Handling the Retrieval-Augmented Generation (RAG) workflow.
- Managing chat history in Amazon DynamoDB.
- Synchronizing user information from Amazon Cognito to DynamoDB.

## AWS Lambda Architecture within the System

The key Lambda functions used include:

| Lambda Function | Functionality |
| --- | --- |
| `rds-init-dev` | Initializes PostgreSQL, enables `pgvector`, and creates the `document_chunks` table |
| `rds-vector-insert-dev` | Writes content and vector embeddings to Amazon RDS |
| `create-vector-dev` | Calls Amazon Bedrock to generate 1024-dimensional vector embeddings |
| `rds-vector-search-dev` | Searches for the nearest document chunks using vector similarity |
| `ChatbotRAG-dev` | Orchestrates the RAG Q&A workflow |
| `user-post-confirmation-dev` | Synchronizes Amazon Cognito users to the `Users-dev` table | ## Chatbot RAG processing flow

## Luồng đồng bộ người dùng

{{< mermaid >}}
graph LR;
    USER[Đăng ký người dùng] --> COGNITO[Amazon Cognito];
    COGNITO --> CONFIRM[Xác nhận tài khoản];
    CONFIRM --> LAMBDA[user-post-confirmation-dev];
    LAMBDA --> USERS[Users-dev];
{{< /mermaid >}}

## Vector data generation flow

{{< mermaid >}}
flowchart LR 
TEXT[Document Text] 
CREATE[create-vector-dev] 
TITAN[Amazon Titan Text Embeddings V2] 
VECTOR[Vector 1024] 
INSERT[rds-vector-insert-dev] 
RDS[(Amazon RDS PostgreSQL)] 
TABLE[document_chunks] 

TEXT --> CREATE 
CREATE --> TITAN 
TITAN --> VECTOR 
VECTOR --> INSERT 
INSERT --> RDS 
RDS --> TABLE
{{< /mermaid >}}

## User sync stream

{{< mermaid >}}
flowchart LR 
USER[User Sign Up] 
COGNITO[Amazon Cognito] 
CONFIRM[Account Confirmation] 
LAMBDA[user-post-confirmation-dev] 
USERS[(Users-dev)] 

USER --> COGNITO 
COGNITO --> CONFIRM 
CONFIRM --> LAMBDA 
LAMBDA --> USERS
{{< /mermaid >}}

## Implementation content

The AWS Lambda section is divided into the following contents:

- **5.4.5.1. General configuration of AWS Lambda**
- **5.4.5.2. Lambda connects Amazon RDS**
- **5.4.5.3. Lambda creates Vector Embedding**
- **5.4.5.4. Lambda Chatbot RAG**
- **5.4.5.5. User synchronization Lambda**

> **Result:** AWS Lambda handles processing and service integration within the Document Chatbot system's backend.