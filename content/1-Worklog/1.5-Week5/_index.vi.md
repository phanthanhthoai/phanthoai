---
title: "Worklog Tuần 5"
date: 2026-08-08
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

**Thời gian:** 20/07/2026 - 26/07/2026

### Mục tiêu tuần

- Hiểu cách xây dựng backend theo kiến trúc Serverless với AWS Lambda.
- Tạo IAM Role và Policy phù hợp cho từng Lambda Function.
- Xây dựng các chức năng đọc và ghi lịch sử trò chuyện trên Amazon DynamoDB.
- Kết nối AWS Lambda với Amazon DynamoDB.
- Kết nối AWS Lambda với Amazon RDS PostgreSQL trong VPC.
- Biết cách kiểm tra và xử lý các lỗi liên quan đến IAM, Environment Variables, VPC và thư viện phụ thuộc.

### Nhật ký công việc

| Ngày | Công việc thực hiện | Kết quả | Nguồn tài liệu / Workshop |
|---|---|---|---|
| 20/07/2026 | Tạo IAM Role và Policy cho các AWS Lambda Function. | Lambda có các quyền cần thiết để truy cập DynamoDB, RDS, Secrets Manager và các dịch vụ liên quan. | [Workshop 5.4.5.1 - Cấu hình chung AWS Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.1-lambda-general-configuration/) |
| 21/07/2026 | Xây dựng Lambda tạo tin nhắn mới và lưu dữ liệu vào `ChatHistory-dev`. | Hoàn thành chức năng tạo dữ liệu lịch sử trò chuyện trên DynamoDB. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 22/07/2026 | Xây dựng Lambda truy vấn lịch sử trò chuyện theo phiên chat. | Có thể lấy danh sách tin nhắn của một phiên trò chuyện từ `ChatHistory-dev`. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 23/07/2026 | Xây dựng Lambda cập nhật nội dung tin nhắn. | Có thể cập nhật dữ liệu tin nhắn đã lưu trong DynamoDB. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 24/07/2026 | Xây dựng Lambda xóa tin nhắn khỏi lịch sử trò chuyện. | Hoàn thành luồng thao tác dữ liệu trên bảng `ChatHistory-dev`. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 25/07/2026 | Cấu hình Lambda kết nối Amazon RDS PostgreSQL trong VPC. | Lambda có thể truy cập PostgreSQL thông qua Private Subnet và Security Group của hệ thống. | [Workshop 5.4.5.2 - Lambda kết nối Amazon RDS](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.2-rds-lambda/) |
| 26/07/2026 | Kiểm tra và xử lý các lỗi IAM, Environment Variables, VPC và thư viện kết nối PostgreSQL. | Khắc phục các lỗi quyền truy cập, cấu hình mạng và dependency để Lambda hoạt động ổn định. | [Workshop 5.4.5.1 - Cấu hình chung AWS Lambda](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.1-lambda-general-configuration/) |

### Tổng kết tuần

- Hoàn thành các chức năng xử lý lịch sử trò chuyện với Amazon DynamoDB.
- Cấu hình IAM Role và Policy cho AWS Lambda.
- Kết nối thành công Lambda với Amazon DynamoDB và Amazon RDS PostgreSQL.
- Hiểu cách Lambda hoạt động trong Amazon VPC khi truy cập cơ sở dữ liệu private.
- Xử lý được các lỗi liên quan đến IAM, Environment Variables, Security Group và Python dependency.
- Chuẩn bị nền tảng Lambda để tiếp tục triển khai vector embedding và semantic search ở tuần tiếp theo.