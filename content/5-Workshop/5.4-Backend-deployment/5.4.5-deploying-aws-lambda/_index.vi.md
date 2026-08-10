---
title: "Triển khai AWS Lambda"
weight: 5
chapter: false
pre: "<b>5.4.5. </b>"
---

# TRIỂN KHAI AWS LAMBDA

AWS Lambda đóng vai trò là lớp logic nghiệp vụ backend chính cho hệ thống Chatbot Tài liệu.

Thay vì triển khai một máy chủ backend chạy liên tục, hệ thống chia nhỏ các chức năng thành nhiều hàm Lambda độc lập. Mỗi hàm đảm nhận một tác vụ cụ thể, chẳng hạn như:

- Khởi tạo cơ sở dữ liệu PostgreSQL.
- Ghi các vector embedding vào Amazon RDS.
- Tạo vector embedding bằng Amazon Bedrock.
- Thực hiện tìm kiếm vector trong PostgreSQL sử dụng `pgvector`.
- Xử lý quy trình Retrieval-Augmented Generation (RAG).
- Quản lý lịch sử trò chuyện trong Amazon DynamoDB.
- Đồng bộ hóa thông tin người dùng từ Amazon Cognito sang DynamoDB.

## Kiến trúc AWS Lambda trong Hệ thống

Các hàm Lambda chính được sử dụng bao gồm:

| Hàm Lambda | Chức năng |
| --- | --- |
| `rds-init-dev` | Khởi tạo PostgreSQL, kích hoạt `pgvector` và tạo bảng `document_chunks` |
| `rds-vector-insert-dev` | Ghi nội dung và vector embedding vào Amazon RDS |
| `create-vector-dev` | Gọi Amazon Bedrock để tạo vector embedding 1024 chiều |
| `rds-vector-search-dev` | Tìm kiếm các đoạn tài liệu gần nhất dựa trên độ tương đồng vector |
| `ChatbotRAG-dev` | Điều phối quy trình hỏi đáp RAG |
| `user-post-confirmation-dev` | Đồng bộ hóa người dùng Amazon Cognito sang bảng `Users-dev` | ## Quy trình xử lý của Chatbot RAG

{{< mermaid >}}
flowchart LR
USER[Câu hỏi của người dùng]
RAG[ChatbotRAG-dev]
TITAN[Amazon Titan Embeddings]
SEARCH[rds-vector-search-dev]
RDS[(Amazon RDS PostgreSQL)]
CHUNKS[Top K đoạn văn bản (chunks)]
NOVA[Amazon Nova Lite]
ANSWER[Câu trả lời]
HISTORY[(ChatHistory-dev)]

USER --> RAG
RAG --> TITAN
TITAN --> SEARCH
SEARCH --> RDS
RDS --> CHUNKS
CHUNKS --> RAG
RAG --> NOVA
NOVA --> ANSWER
ANSWER --> HISTORY
{{< /mermaid >}}

## Quy trình tạo dữ liệu vector

{{< mermaid >}}
flowchart LR
TEXT[Văn bản tài liệu]
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

## Luồng đồng bộ hóa người dùng

## Luồng đồng bộ người dùng

{{< mermaid >}}
graph LR;
    USER[Đăng ký người dùng] --> COGNITO[Amazon Cognito];
    COGNITO --> CONFIRM[Xác nhận tài khoản];
    CONFIRM --> LAMBDA[user-post-confirmation-dev];
    LAMBDA --> USERS[Users-dev];
{{< /mermaid >}}

## Nội dung triển khai

Phần AWS Lambda được chia thành các nội dung sau:

- **5.4.5.1. Cấu hình chung của AWS Lambda**
- **5.4.5.2. Lambda kết nối với Amazon RDS**
- **5.4.5.3. Lambda tạo Vector Embedding**
- **5.4.5.4. Lambda Chatbot RAG**
- **5.4.5.5. Lambda đồng bộ hóa người dùng**

> **Kết quả:** AWS Lambda đảm nhiệm việc xử lý và tích hợp dịch vụ trong phần backend của hệ thống Document Chatbot.