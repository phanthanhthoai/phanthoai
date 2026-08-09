---
title: "Week 7 Worklog"
date: 2026-08-08
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---


**Period:** 03/08/2026 - 09/08/2026

### Weekly Objectives

- Verify the accuracy of the vector search function.
- Measure and evaluate query performance on Amazon RDS PostgreSQL.
- Measure and evaluate query performance on Amazon DynamoDB.
- Analyze metrics: min, max, average, median, and p95 latency.
- Implement user registration and login functionality using Amazon Cognito.
- Test key system components prior to finalizing the report.

### Work Log

| Date | Task Performed | Result | Documentation / Workshop |
|---|---|---|---|
| 03/08/2026 | Conducted 50 vector searches on Amazon RDS PostgreSQL to test `pgvector` query capabilities. | Completed 50 test runs; average latency was approximately 50.398 ms, and expected results were retrieved accurately. | [Workshop 5.5 - System Testing](/vi/5-workshop/5.5-system-testing/) |
| 04/08/2026 | Executed 100 queries for chat history on the Amazon DynamoDB `ChatHistory-dev` table. | Completed 100 queries with a 0% error rate; average latency was approximately 35.172 ms. | [Workshop 5.5 - System Testing](/vi/5-workshop/5.5-system-testing/) |
| 05/08/2026 | Aggregated and analyzed latency metrics (min, max, average, median, p95) for RDS and DynamoDB. | Data available to evaluate the responsiveness of the two storage options within the system. | [Workshop 5.5 - System Testing](/vi/5-workshop/5.5-system-testing/) |
| 06/08/2026 | Create and configure an Amazon Cognito User Pool for user authentication. | User Pool and App Client configured for the Document Chatbot system. | [Workshop 5.4.1 - Amazon Cognito](/vi/5-workshop/5.4-backend-deployment/5.4.1-creating-amazon-cognito/) |
| 07/08/2026 | Test the registration, account verification, and login processes using the Amazon Cognito authentication interface. | Users can successfully register, verify accounts, and log in. | [Workshop 5.4.1 - Amazon Cognito](/vi/5-workshop/5.4-backend-deployment/5.4.1-creating-amazon-cognito/) |
| 08/08/2026 | Configure the Lambda Post Confirmation function to synchronize user information from Amazon Cognito to the `Users-dev` table. | User information is synchronized to Amazon DynamoDB after account verification. | [Workshop 5.4.5.5 - User Synchronization Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.5-user-lambda/) |
| 09/08/2026 | Test the `ChatbotRAG-dev` workflow integrating Amazon Bedrock, vector search, and Amazon RDS PostgreSQL. | RAG workflow tested: from user query and Top-K document chunk search to answer generation. | [Workshop 5.4.5.4 - Chatbot RAG Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.4-chatbot-rag/) | ### Weekly Summary

- Completed performance testing for Amazon RDS PostgreSQL and Amazon DynamoDB.
- Evaluated system latency metrics, including min, max, average, median, and p95 values.
- Completed user authentication configuration using Amazon Cognito.
- Successfully tested the user registration and login processes.
- Synchronized user information from Amazon Cognito to the `Users-dev` table.
- Tested the RAG workflow integrating Amazon Bedrock, AWS Lambda, and Amazon RDS PostgreSQL.
- Finalized key technical functionalities ahead of the workshop consolidation and reporting phase.