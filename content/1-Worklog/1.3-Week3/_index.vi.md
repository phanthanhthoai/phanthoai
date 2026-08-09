---
title: "Worklog Tuần 3"
date: 2026-08-08
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

**Thời gian:** 06/07/2026 - 12/07/2026

### Mục tiêu tuần

- Hiểu đặc điểm của Amazon RDS, Amazon DynamoDB và Amazon Aurora.
- Phân tích yêu cầu của hệ thống hỏi đáp tài liệu thông minh.
- Xác định các chức năng và thành phần chính của Capstone Project.
- Thiết kế kiến trúc tổng thể sử dụng các dịch vụ AWS.
- Thiết kế cơ sở dữ liệu phù hợp để lưu tài liệu, vector embedding và lịch sử trò chuyện.

### Nhật ký công việc

| Ngày | Công việc thực hiện | Kết quả | Nguồn tài liệu / Workshop |
|---|---|---|---|
| 06/07/2026 | Tìm hiểu Amazon RDS, Amazon DynamoDB và Amazon Aurora. | Phân biệt được cơ sở dữ liệu quan hệ và NoSQL, đồng thời hiểu vai trò của từng dịch vụ trong hệ thống. | AWS Documentation - Amazon RDS, Amazon DynamoDB, Amazon Aurora |
| 07/07/2026 | Phân tích yêu cầu dự án chatbot hỏi đáp tài liệu. | Xác định các thành phần chính của hệ thống như lưu trữ tài liệu, xử lý nội dung, tạo embedding, tìm kiếm vector và lịch sử trò chuyện. | [Workshop 5.1 - Tổng quan hệ thống](/vi/5-workshop/5.1-workshop-overview/) |
| 08/07/2026 | Thiết kế kiến trúc sử dụng Amazon S3, Amazon Textract, AWS Lambda, Amazon Bedrock, Amazon RDS và Amazon DynamoDB. | Hoàn thành kiến trúc tổng quan của Capstone Project và xác định luồng dữ liệu giữa các dịch vụ AWS. | [Workshop 5.1 - Kiến trúc tổng thể hệ thống](/vi/5-workshop/5.1-workshop-overview/) |
| 09/07/2026 | Thiết kế bảng `documents` và `document_chunks` để lưu thông tin tài liệu và các đoạn nội dung. | Xác định cấu trúc dữ liệu phục vụ lưu trữ tài liệu và vector embedding. | [Workshop 5.4.4 - Amazon RDS PostgreSQL và pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 10/07/2026 | Lựa chọn PostgreSQL với extension `pgvector` để lưu trữ vector embedding. | Xác định giải pháp lưu vector embedding 1.024 chiều và hỗ trợ semantic search trong PostgreSQL. | [Workshop 5.4.4 - Amazon RDS PostgreSQL và pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 11/07/2026 | Thiết kế bảng DynamoDB `ChatHistory-dev` và các khóa phục vụ truy vấn lịch sử trò chuyện. | Hoàn thành cấu trúc lưu trữ lịch sử chat và xác định cách truy vấn theo phiên trò chuyện. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |

### Tổng kết tuần

- Hoàn thành phân tích yêu cầu của Capstone Project.
- Xác định kiến trúc tổng thể sử dụng các dịch vụ AWS.
- Lựa chọn Amazon RDS PostgreSQL với `pgvector` để lưu vector embedding.
- Lựa chọn Amazon DynamoDB để lưu dữ liệu lịch sử trò chuyện.
- Hoàn thành thiết kế cơ sở dữ liệu làm nền tảng cho giai đoạn triển khai thực tế ở các tuần tiếp theo.