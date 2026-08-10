---
title: "Chatbot RAG Lambda"
weight: 4
chapter: false
pre: "<b>5.4.5.4. </b>"
---

# LAMBDA CHATBOT RAG

The `ChatbotRAG-dev` Lambda function orchestrates the system's Retrieval-Augmented Generation (RAG) workflow.

When a user asks a question, the system generates an embedding for the question, retrieves relevant document chunks from RDS, and uses Amazon Nova Lite to generate an answer.

## Processing Workflow

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

## Lambda Configuration

Function:

```text
ChatbotRAG-dev
```

## Required IAM Role Permissions:

```text
bedrock:InvokeModel
lambda:InvokeFunction
```

Models used:
```text
Embedding:
amazon.titan-embed-text-v2:0
Chat:
Amazon Nova Lite
```

## Operation

Upon receiving a question:

1. Generate an embedding for the question.
2. Invoke `rds-vector-search-dev`.
3. Retrieve the Top K document chunks.
4. Feed the context and the question into Amazon Nova Lite.
5. Generate the answer.
6. Save the chat history.

The Lambda function does not access RDS directly; instead, it invokes:

`rds-vector-search-dev`

to perform the vector search. Place this file at:

```text
5.4.5-deploying-aws-lambda/
└── 5.4.5.4-chatbot-rag/
└── _index.vi.md

The only difference compared to the file you sent is that it includes the full Front Matter at the beginning: