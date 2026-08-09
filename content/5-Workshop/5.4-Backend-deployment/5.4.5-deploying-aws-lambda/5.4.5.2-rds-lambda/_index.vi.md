---
title: "Lambda kết nối Amazon RDS"
weight: 2
chapter: false
pre: "<b>5.4.5.2. </b>"
---

# KẾT NỐI AMAZON RDS

Nhóm Lambda này chịu trách nhiệm khởi tạo, lưu trữ và tìm kiếm vector trên Amazon RDS PostgreSQL với `pgvector`.

Các Lambda gồm:

```text
rds-init-dev
rds-vector-insert-dev
rds-vector-search-dev
```

### Luồng xử lý

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

## Cấu hình Lambda

Các Lambda sử dụng:

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

Các Lambda này sử dụng thư viện:

pg8000

để kết nối PostgreSQL.

## rds-init-dev

Lambda rds-init-dev được sử dụng để:

Enable pgvector
Create document_chunks
Create Indexes

Vector được cấu hình:

embedding VECTOR(1024)

Quá trình tạo database đã được trình bày chi tiết trong phần Amazon RDS PostgreSQL và pgvector.

Kiểm thử

Chọn:

rds-init-dev
→ Test

Kết quả:

statusCode       = 200
status           = success
database         = chatbot_db
pgvectorVersion  = 0.8.2
table            = document_chunks
vectorDimension  = 1024

![rds init](images/5.7-Lambda/rdsinit.png)

## rds-vector-insert-dev

Lambda này nhận:

documentId
userId
fileName
pageNumber
chunkIndex
content
embedding
metadata

và lưu vào:

document_chunks
Kiểm thử
rds-vector-insert-dev
→ Test

Kết quả thành công:

{
  "status": "success",
  "insertedOrUpdated": true
}

## rds-vector-search-dev

Lambda này nhận query embedding và tìm các document chunk gần nhất.
Truy vấn sử dụng:

ORDER BY embedding <=> CAST(%s AS vector)
LIMIT %s

Kết quả trả về:

documentId
fileName
pageNumber
chunkIndex
content
similarity

