---
title: "Week 5 Worklog"
date: 2026-08-08
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

**Timeframe:** 20/07/2026 - 26/07/2026

### Weekly Objectives

- Understand how to build a backend using a Serverless architecture with AWS Lambda.
- Create appropriate IAM Roles and Policies for each Lambda Function.
- Implement functions to read and write chat history to Amazon DynamoDB.
- Connect AWS Lambda to Amazon DynamoDB.
- Connect AWS Lambda to Amazon RDS PostgreSQL within a VPC.
- Learn how to troubleshoot and handle errors related to IAM, Environment Variables, VPC, and dependencies.

### Worklog

| Date | Tasks Performed | Results | Resources / Workshop |
|---|---|---|---|
| 20/07/2026 | Created IAM Roles and Policies for AWS Lambda Functions. | Lambda has the necessary permissions to access DynamoDB, RDS, Secrets Manager, and related services. | [Workshop 5.4.5.1 - AWS Lambda General Configuration](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.1-lambda-general-configuration/) |
| 21/07/2026 | Built a Lambda function to create new messages and save data to `ChatHistory-dev`. | Completed the function to create chat history data in DynamoDB. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 22/07/2026 | Built a Lambda function to query chat history by chat session. | Able to retrieve the list of messages for a specific chat session from `ChatHistory-dev`. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 23/07/2026 | Build a Lambda function to update message content. | Ability to update stored message data in DynamoDB. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 24/07/2026 | Build a Lambda function to delete messages from chat history. | Complete the data operation workflow for the `ChatHistory-dev` table. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 25/07/2026 | Configure Lambda to connect to Amazon RDS PostgreSQL within the VPC. | Lambda can access PostgreSQL via the Private Subnet and system Security Group. | [Workshop 5.4.5.2 - Lambda connecting to Amazon RDS](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.2-rds-lambda/) |
| 26/07/2026 | Troubleshoot and resolve errors related to IAM, Environment Variables, VPC, and PostgreSQL connection libraries. | Fix access permission, network configuration, and dependency issues to ensure stable Lambda operation. | [Workshop 5.4.5.1 - AWS Lambda General Configuration](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.1-lambda-general-configuration/) |

### Weekly Summary

- Completed chat history processing functions using Amazon DynamoDB.
- Configured IAM Roles and Policies for AWS Lambda. - Successfully connected Lambda to Amazon DynamoDB and Amazon RDS PostgreSQL.
- Understood how Lambda operates within an Amazon VPC when accessing private databases.
- Resolved issues related to IAM, environment variables, security groups, and Python dependencies.
- Prepared the Lambda foundation for the subsequent implementation of vector embeddings and semantic search.