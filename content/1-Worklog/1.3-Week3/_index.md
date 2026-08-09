---
title: "Week 3 Worklog"
date: 2026-08-08
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

**Timeframe:** 06/07/2026 - 12/07/2026

### Weekly Objectives

- Understand the characteristics of Amazon RDS, Amazon DynamoDB, and Amazon Aurora.
- Analyze the requirements for the intelligent document Q&A system.
- Identify the key functions and components of the Capstone Project.
- Design the overall architecture using AWS services.
- Design a suitable database for storing documents, vector embeddings, and chat history.

### Worklog

| Date | Tasks Performed | Results | Resources / Workshop |
|---|---|---|---|
| 06/07/2026 | Research Amazon RDS, Amazon DynamoDB, and Amazon Aurora. | Distinguished between relational and NoSQL databases and understood the role of each service within the system. | AWS Documentation - Amazon RDS, Amazon DynamoDB, Amazon Aurora |
| 07/07/2026 | Analyze requirements for the document Q&A chatbot project. | Identified key system components such as document storage, content processing, embedding generation, vector search, and chat history. | [Workshop 5.1 - System Overview](/vi/5-workshop/5.1-workshop-overview/) |
| 08/07/2026 | Design architecture using Amazon S3, Amazon Textract, AWS Lambda, Amazon Bedrock, Amazon RDS, and Amazon DynamoDB. | Completed the high-level architecture for the Capstone Project and defined data flows between AWS services. | [Workshop 5.1 - Overall System Architecture](/vi/5-workshop/5.1-workshop-overview/) |
| 09/07/2026 | Design the `documents` and `document_chunks` tables to store document information and content segments. | Define the data structure for storing documents and vector embeddings. | [Workshop 5.4.4 - Amazon RDS PostgreSQL and pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 10/07/2026 | Select PostgreSQL with the `pgvector` extension for storing vector embeddings. | Determine the solution for storing 1,024-dimensional vector embeddings and supporting semantic search within PostgreSQL. | [Workshop 5.4.4 - Amazon RDS PostgreSQL and pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 11/07/2026 | Design the DynamoDB table `ChatHistory-dev` and keys to facilitate chat history queries. | Finalize the chat history storage structure and define query methods based on chat sessions. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |

### Weekly Summary

- Completed the requirements analysis for the Capstone Project.
- Defined the overall architecture utilizing AWS services.
- Selected Amazon RDS PostgreSQL with `pgvector` for storing vector embeddings.
- Selected Amazon DynamoDB for storing chat history data.
- Finalized the database design, establishing the foundation for the actual implementation phase in the coming weeks.