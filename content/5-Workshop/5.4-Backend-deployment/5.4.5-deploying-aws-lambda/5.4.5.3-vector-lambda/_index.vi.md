---
title: "Lambda tạo Vector Embedding"
weight: 3
chapter: false
pre: "<b>5.4.5.3. </b>"
---

# LAMBDA TẠO VECTOR EMBEDDING

Lambda `create-vector-dev` được sử dụng để chuyển nội dung văn bản thành vector embedding bằng Amazon Bedrock.

Model được sử dụng:

```text
amazon.titan-embed-text-v2:0
```

## Quy trình tạo dữ liệu Vector

{{< mermaid >}}
graph LR;
    TEXT[Văn bản tài liệu] --> CREATE[create-vector-dev];
    CREATE --> TITAN[Amazon Titan Text Embeddings V2];
    TITAN --> VECTOR[Vector 1024];
    VECTOR --> INSERT[rds-vector-insert-dev];
    INSERT --> RDS[Amazon RDS PostgreSQL];
    RDS --> TABLE[document_chunks];
{{< /mermaid >}}

## Cấu hình Lambda

Tạo Lambda:
```texxt
Function name:
create-vector-dev

Runtime:
Python

IAM Role cần quyền:

bedrock:InvokeModel
lambda:InvokeFunction

Environment Variables:

BEDROCK_REGION = us-east-1
EMBEDDING_MODEL_ID = amazon.titan-embed-text-v2:0
```
Lambda này không kết nối trực tiếp Amazon RDS nên không cần cấu hình VPC của RDS.
