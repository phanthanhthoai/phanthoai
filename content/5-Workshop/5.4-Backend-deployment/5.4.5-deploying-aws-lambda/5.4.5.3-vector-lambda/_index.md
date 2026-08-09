---
title: ""
weight: 3
chapter: false
pre: "<b>5.4.5.3. </b>"
---

# VECTOR EMBEDDING GENERATION LAMBDA

The `create-vector-dev` Lambda is used to convert text content into vector embeddings using Amazon Bedrock.

Model used:

```text
amazon.titan-embed-text-v2:0
```
## Processing Flow

{{< mermaid >}}
graph LR;
    TEXT[Văn bản tài liệu] --> CREATE[create-vector-dev];
    CREATE --> TITAN[Amazon Titan Text Embeddings V2];
    TITAN --> VECTOR[Vector 1024];
    VECTOR --> INSERT[rds-vector-insert-dev];
    INSERT --> RDS[Amazon RDS PostgreSQL];
    RDS --> TABLE[document_chunks];
{{< /mermaid >}}

## Lambda Configuration

Create Lambda:
```text
Function name:
create-vector-dev

Runtime:
Python

IAM Role required permissions:

bedrock:InvokeModel
lambda:InvokeFunction

Environment Variables:

BEDROCK_REGION = us-east-1
EMBEDDING_MODEL_ID = amazon.titan-embed-text-v2:0
```
This Lambda does not connect directly to Amazon RDS, so RDS VPC configuration is not required.