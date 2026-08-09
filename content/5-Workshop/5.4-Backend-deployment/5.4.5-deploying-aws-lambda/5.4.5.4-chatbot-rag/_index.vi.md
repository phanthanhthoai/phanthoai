---
title: "Lambda Chatbot RAG"
weight: 4
chapter: false
pre: "<b>5.4.5.4. </b>"
---

# LAMBDA CHATBOT RAG

Lambda `ChatbotRAG-dev` điều phối luồng Retrieval-Augmented Generation của hệ thống.

Khi người dùng đặt câu hỏi, hệ thống tạo embedding cho câu hỏi, tìm các document chunk liên quan trong RDS và sử dụng Amazon Nova Lite để sinh câu trả lời.

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

## Cấu hình Lambda

Function:

```text
ChatbotRAG-dev
```
## IAM Role cần quyền:

```text
bedrock:InvokeModel
lambda:InvokeFunction
```

Các model được sử dụng:
```text
Embedding:
amazon.titan-embed-text-v2:0
Chat:
Amazon Nova Lite
```

## Hoạt động

Khi nhận câu hỏi:

1. Tạo embedding cho câu hỏi.
2. Gọi rds-vector-search-dev.
3. Nhận Top K document chunks.
4. Đưa context và câu hỏi vào Amazon Nova Lite.
5. Sinh câu trả lời.
6. Lưu lịch sử trò chuyện.

Lambda không truy cập trực tiếp RDS mà gọi:

rds-vector-search-dev

để thực hiện vector search.


File này bạn đặt tại:

```text
5.4.5-deploying-aws-lambda/
└── 5.4.5.4-chatbot-rag/
    └── _index.vi.md

Điểm khác duy nhất so với file bạn gửi là phần đầu giờ có Front Matter đầy đủ: