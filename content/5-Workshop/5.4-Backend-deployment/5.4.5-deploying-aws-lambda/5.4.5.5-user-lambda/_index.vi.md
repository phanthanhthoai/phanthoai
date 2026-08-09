---
title: "Lambda User"
weight: 5
chapter: false
pre: "<b>5.4.5.5. </b>"
---

# LAMBDA ĐỒNG BỘ NGƯỜI DÙNG

Lambda `user-post-confirmation-dev` được sử dụng để đồng bộ thông tin người dùng từ Amazon Cognito vào Amazon DynamoDB.

Lambda được cấu hình làm **Post Confirmation Trigger** của Cognito User Pool.

## Luồng xử lý

## Luồng xử lý Chatbot RAG

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

## Cấu hình Lambda

Function:

```text
user-post-confirmation-dev

-Environment Variable:

-USERS_TABLE_NAME = Users-dev

-Lambda cần quyền:

dynamodb:UpdateItem

-Amazon Cognito cần quyền:

lambda:InvokeFunction
```
để gọi Lambda sau khi người dùng xác nhận tài khoản.

## Cấu hình Cognito Trigger

Mở Amazon Cognito User Pool.

1. Chọn:

Extensions
→ Lambda triggers

2. Tại Post Confirmation chọn:

user-post-confirmation-dev

3. Sau đó lưu cấu hình.

4. Luồng kích hoạt:

User Confirmed
→ Cognito Post Confirmation
→ user-post-confirmation-dev
→ Users-dev

## Dữ liệu người dùng

Lambda lấy các thuộc tính từ Cognito như:

sub
email
name

Trong đó:

sub

được sử dụng làm userId của người dùng.

Thông tin được lưu vào:

Users-dev