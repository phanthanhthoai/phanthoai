---
title: "Worklog Tuần 4"
date: 2026-08-08
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

**Thời gian:** 13/07/2026 - 19/07/2026

### Mục tiêu tuần

- Khởi tạo và cấu hình Amazon RDS PostgreSQL cho dự án.
- Kích hoạt extension `pgvector` để hỗ trợ lưu trữ và tìm kiếm vector.
- Xây dựng các bảng `documents` và `document_chunks`.
- Khởi tạo Amazon DynamoDB để lưu trữ lịch sử trò chuyện.
- Thiết kế Partition Key và Sort Key phục vụ truy vấn dữ liệu.
- Cấu hình VPC, Subnet và Security Group để bảo vệ cơ sở dữ liệu.

### Nhật ký công việc

| Ngày | Công việc thực hiện | Kết quả | Nguồn tài liệu / Workshop |
|---|---|---|---|
| 13/07/2026 | Khởi tạo Amazon RDS PostgreSQL phục vụ lưu trữ dữ liệu tài liệu và vector embedding. | Tạo được database PostgreSQL phục vụ Capstone Project. | [Workshop 5.4.4 - Amazon RDS PostgreSQL và pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 14/07/2026 | Cấu hình VPC, Private Subnet và Security Group cho Amazon RDS. | Thiết lập được môi trường mạng và giới hạn quyền truy cập đến database. | [Workshop 5.4.4 - Cấu hình mạng cho Amazon RDS](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 15/07/2026 | Kích hoạt extension `pgvector` trên PostgreSQL. | PostgreSQL hỗ trợ lưu trữ và thực hiện tìm kiếm trên dữ liệu vector. | [Workshop 5.4.4 - Kích hoạt pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 16/07/2026 | Tạo các bảng `documents` và `document_chunks` phục vụ lưu trữ dữ liệu tài liệu. | Hoàn thành cấu trúc cơ sở dữ liệu phục vụ lưu nội dung và vector embedding. | [Workshop 5.4.4 - Amazon RDS PostgreSQL và pgvector](/vi/5-workshop/5.4-backend-deployment/5.4.4-creating-amazon-rds-pgvector/) |
| 17/07/2026 | Khởi tạo bảng DynamoDB `ChatHistory-dev`. | Có nơi lưu trữ dữ liệu lịch sử trò chuyện của người dùng. | [Workshop 5.4.2 - Amazon DynamoDB](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |
| 18/07/2026 | Cấu hình Partition Key, Sort Key và thêm dữ liệu mẫu để kiểm tra cấu trúc bảng. | Có thể lưu và truy vấn tin nhắn theo phiên trò chuyện. | [Workshop 5.4.2 - Thiết kế bảng ChatHistory-dev](/vi/5-workshop/5.4-backend-deployment/5.4.2-creating-amazon-dynamodb/) |

### Tổng kết tuần

- Khởi tạo thành công Amazon RDS PostgreSQL và Amazon DynamoDB.
- Cấu hình VPC, Subnet và Security Group cho cơ sở dữ liệu.
- Kích hoạt extension `pgvector` trên PostgreSQL.
- Hoàn thành cấu trúc dữ liệu phục vụ lưu trữ tài liệu, vector embedding và lịch sử trò chuyện.
- Chuẩn bị cơ sở dữ liệu để các AWS Lambda Function có thể kết nối và xử lý dữ liệu trong giai đoạn tiếp theo.