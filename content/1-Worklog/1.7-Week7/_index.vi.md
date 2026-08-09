---
title: "Worklog Tuần 7"
date: 2026-08-08
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---


**Thời gian:** 03/08/2026 - 09/08/2026

### Mục tiêu tuần

- Kiểm tra tính chính xác của chức năng tìm kiếm vector.
- Đo và đánh giá hiệu năng truy vấn trên Amazon RDS PostgreSQL.
- Đo và đánh giá hiệu năng truy vấn trên Amazon DynamoDB.
- Phân tích các chỉ số min, max, average, median và p95 latency.
- Xây dựng chức năng đăng ký và đăng nhập bằng Amazon Cognito.
- Kiểm thử các thành phần chính của hệ thống trước khi hoàn thiện báo cáo.

### Nhật ký công việc

| Ngày | Công việc thực hiện | Kết quả | Nguồn tài liệu / Workshop |
|---|---|---|---|
| 03/08/2026 | Thực hiện 50 lượt tìm kiếm vector trên Amazon RDS PostgreSQL để kiểm tra khả năng truy vấn `pgvector`. | Hoàn thành 50 lượt kiểm thử, độ trễ trung bình khoảng 50,398 ms và kết quả mong đợi được tìm thấy chính xác. | [Workshop 5.5 - Kiểm thử hệ thống](/vi/5-workshop/5.5-system-testing/) |
| 04/08/2026 | Thực hiện 100 lượt truy vấn lịch sử trò chuyện trên bảng `ChatHistory-dev` của Amazon DynamoDB. | Hoàn thành 100 lượt truy vấn với tỷ lệ lỗi 0%, độ trễ trung bình khoảng 35,172 ms. | [Workshop 5.5 - Kiểm thử hệ thống](/vi/5-workshop/5.5-system-testing/) |
| 05/08/2026 | Tổng hợp và phân tích các chỉ số min, max, average, median và p95 latency của RDS và DynamoDB. | Có số liệu để đánh giá khả năng đáp ứng của hai phương án lưu trữ trong hệ thống. | [Workshop 5.5 - Kiểm thử hệ thống](/vi/5-workshop/5.5-system-testing/) |
| 06/08/2026 | Tạo và cấu hình Amazon Cognito User Pool phục vụ xác thực người dùng. | Hoàn thành cấu hình User Pool và App Client cho hệ thống Document Chatbot. | [Workshop 5.4.1 - Amazon Cognito](/vi/5-workshop/5.4-backend-deployment/5.4.1-creating-amazon-cognito/) |
| 07/08/2026 | Kiểm thử quá trình đăng ký, xác nhận tài khoản và đăng nhập bằng giao diện xác thực của Amazon Cognito. | Người dùng có thể đăng ký, xác nhận và đăng nhập thành công. | [Workshop 5.4.1 - Amazon Cognito](/vi/5-workshop/5.4-backend-deployment/5.4.1-creating-amazon-cognito/) |
| 08/08/2026 | Cấu hình Lambda Post Confirmation để đồng bộ thông tin người dùng từ Amazon Cognito sang bảng `Users-dev`. | Sau khi tài khoản được xác nhận, thông tin người dùng có thể được đồng bộ vào Amazon DynamoDB. | [Workshop 5.4.5.5 - Lambda đồng bộ người dùng](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.5-user-lambda/) |
| 09/08/2026 | Kiểm tra luồng `ChatbotRAG-dev` kết hợp Amazon Bedrock, vector search và Amazon RDS PostgreSQL. | Hoàn thành kiểm thử luồng RAG từ câu hỏi, tìm kiếm Top K document chunks đến sinh câu trả lời. | [Workshop 5.4.5.4 - Lambda Chatbot RAG](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.4-chatbot-rag/) |

### Tổng kết tuần

- Hoàn thành kiểm thử hiệu năng Amazon RDS PostgreSQL và Amazon DynamoDB.
- Đánh giá được các chỉ số độ trễ của hệ thống thông qua min, max, average, median và p95.
- Hoàn thành cấu hình xác thực người dùng bằng Amazon Cognito.
- Kiểm thử thành công quá trình đăng ký và đăng nhập.
- Đồng bộ thông tin người dùng từ Amazon Cognito sang bảng `Users-dev`.
- Kiểm thử được luồng RAG kết hợp Amazon Bedrock, AWS Lambda và Amazon RDS PostgreSQL.
- Hoàn thành các chức năng kỹ thuật chính trước giai đoạn tổng hợp Workshop và báo cáo.