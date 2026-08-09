---
title: "Lambda Connecting to Amazon RDS"
weight: 2
chapter: false
pre: "<b>5.4.5.2. </b>"
---

# CONNECTING TO AMAZON RDS

This group of Lambda functions is responsible for initialization, storage, and vector search operations on Amazon RDS PostgreSQL using `pgvector`.

The Lambda functions include:

```text
rds-init-dev
rds-vector-insert-dev
rds-vector-search-dev
```

### Processing Flow

{{< mermaid >}}
flowchart LR
INIT[rds-init-dev]
INSERT[rds-vector-insert-dev]
SEARCH[rds-vector-search-dev]
RDS[(RDS PostgreSQL)]
TABLE[document_chunks]

INIT -->|Initialize| RDS
INSERT -->|Insert Vector| RDS
SEARCH -->|Vector Search| RDS
RDS --> TABLE

{{< /mermaid >}}

## Lambda Configuration

The Lambda functions use:

Runtime: Python

VPC:
document-chatbot-vpc-dev

Security Group:
document-chatbot-lambda-rds-sg

Environment Variables:

DB_HOST
DB_PORT
DB_NAME
DB_SECRET_ARN

These Lambda functions use the library:

pg8000

to connect to PostgreSQL.

## rds-init-dev

The rds-init-dev Lambda function is used to:

Enable pgvector
Create document_chunks
Create Indexes

Vector configuration:

embedding VECTOR(1024)

The database creation process has been detailed in the Amazon RDS PostgreSQL and pgvector section. Testing

Select:

rds-init-dev
→ Test

Result:

statusCode       = 200
status           = success
database         = chatbot_db
pgvectorVersion  = 0.8.2
table            = document_chunks
vectorDimension  = 1024

![rds init](images/5.7-Lambda/rdsinit.png)

## rds-vector-insert-dev

This Lambda receives:

documentId
userId
fileName
pageNumber
chunkIndex
content
embedding
metadata

and saves them to:

document_chunks
Testing
rds-vector-insert-dev
→ Test

Success result:

{
"status": "success",
"insertedOrUpdated": true
}

## rds-vector-search-dev

This Lambda receives a query embedding and finds the nearest document chunks.
The query uses:

ORDER BY embedding <=> CAST(%s AS vector)
LIMIT %s

Returned results:

documentId
fileName
pageNumber
chunkIndex
content
similarity