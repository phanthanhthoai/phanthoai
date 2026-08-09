---
title: "Week 6 Worklog"
date: 2026-08-08
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

**Period:** July 27, 2026 – August 2, 2026

### Weekly Objectives

- Understand the concepts of Generative AI, Large Language Models, Embeddings, and Retrieval-Augmented Generation (RAG).
- Understand the role of Amazon Textract in the system's document processing workflow.
- Use Amazon Bedrock to generate vector embeddings from text content.
- Store vector embeddings in Amazon RDS PostgreSQL using `pgvector`.
- Implement semantic search functionality to retrieve relevant document segments.
- Generate test data to evaluate the performance of Amazon RDS and Amazon DynamoDB.

### Work Log

| Date | Tasks Performed | Results | Resources / Workshop |
|---|---|---|---|
| July 27, 2026 | Studied Generative AI, Large Language Models, and the Retrieval-Augmented Generation (RAG) architecture. | Understood the processing flow: from user query to embedding generation, retrieval of relevant content, and answer generation. | [Workshop 5.4.5.4 - Lambda Chatbot RAG](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.4-chatbot-rag/) |
| July 28, 2026 | Studied Amazon Textract and its role in the document content extraction process. | Understood how document content can be converted into text data for further processing within the RAG pipeline. | ​​AWS Documentation - Amazon Textract |
| July 29, 2026 | Selected the `amazon.titan-embed-text-v2:0` model on Amazon Bedrock to generate vector embeddings. | Determine the system's embedding model with a 1,024-dimensional vector size. | [Workshop 5.4.5.3 - Vector Embedding Generation Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.3-vector-lambda/) |
| 30/07/2026 | Build a Lambda function to generate embedding vectors and store them in Amazon RDS PostgreSQL. | Text is converted into 1,024-dimensional vectors and stored in the `document_chunks` table. | [Workshop 5.4.5.3 - Vector Embedding Generation Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.3-vector-lambda/) • [Workshop 5.4.5.2 - Amazon RDS Connection Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.2-rds-lambda/) |
| 31/07/2026 | Implement vector search functionality in PostgreSQL using cosine distance. | Enables searching for document chunks with vectors closest to the query vector. | [Workshop 5.4.5.2 - Amazon RDS Connection Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.2-rds-lambda/) |
| 01/08/2026 | Generate and populate Amazon RDS with 2,000 test data vectors. | Establishes a dataset large enough to test vector search functionality and measure query latency. | [Workshop 5.5 - System Testing](/vi/5-workshop/5.5-system-testing/) |
| 02/08/2026 | Create 100 test chat sessions in Amazon DynamoDB, each consisting of 20 messages. | Preparing data for testing chat history query capabilities. | [Workshop 5.5 - System Testing](/vi/5-workshop/5.5-system-testing/) |

### Weekly Summary

- Understood the operating principles of the RAG architecture.
- Selected and utilized Amazon Titan Text Embeddings V2 to generate vector embeddings.
- Completed the workflow for generating and storing 1,024-dimensional vectors in Amazon RDS PostgreSQL.
- Implemented semantic search functionality using `pgvector`.
- Prepared 2,000 test vectors in RDS.
- Prepared 100 chat sessions, each consisting of 20 messages, in DynamoDB.
- Finalized input data for performance benchmarking in the upcoming week.