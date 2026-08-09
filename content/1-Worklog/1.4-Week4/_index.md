---
title: "Worklog Week 4"
date: 2026-08-08
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

**Timeframe:** 13/07/2026 - 19/07/2026

### Weekly Objectives

- Initialize and configure Amazon RDS PostgreSQL for the project.
- Enable the `pgvector` extension to support vector storage and search.
- Create the `documents` and `document_chunks` tables.
- Initialize Amazon DynamoDB to store chat history.
- Design Partition Keys and Sort Keys to facilitate data queries.
- Configure VPC, Subnets, and Security Groups to secure the database.

### Work Log

| Date | Tasks Performed | Outcome | Resources / Workshop |
|---|---|---|---|
| 13/07/2026 | Initialize Amazon RDS PostgreSQL for storing document data and vector embeddings. | Successfully created a PostgreSQL database for the Capstone Project. | [Workshop 5.4.4 - Amazon RDS PostgreSQL and pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 14/07/2026 | Configure VPC, Private Subnet, and Security Group for Amazon RDS. | Established the network environment and restricted database access. | [Workshop 5.4.4 - Network configuration for Amazon RDS](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 15/07/2026 | Enable the `pgvector` extension on PostgreSQL. | PostgreSQL is now capable of storing and searching vector data. | [Workshop 5.4.4 - Enabling pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 16/07/2026 | Create `documents` and `document_chunks` tables for document data storage. | Database structure for storing content and vector embeddings is complete. | [Workshop 5.4.4 - Amazon RDS PostgreSQL and pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 17/07/2026 | Initialize the `ChatHistory-dev` DynamoDB table. | Established storage for user chat history data. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 18/07/2026 | Configure Partition Key and Sort Key; add sample data to verify table structure. | Capable of storing and querying messages by chat session. | [Workshop 5.4.2 - Designing the ChatHistory-dev table](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |

### Weekly Summary

- Successfully initialized Amazon RDS PostgreSQL and Amazon DynamoDB.
- Configured VPC, Subnets, and Security Groups for the databases.
- Enabled the `pgvector` extension on PostgreSQL.
- Completed data structures for storing documents, vector embeddings, and chat history.
- Prepared databases for AWS Lambda functions to connect and process data in the next phase.