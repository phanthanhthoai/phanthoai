---
title: "Worklog Tuần 6"
date: 2026-08-08
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

**Thời gian:** 27/07/2026 - 02/08/2026

### Mục tiêu tuần

- Hiểu các khái niệm Generative AI, Large Language Model, Embedding và Retrieval-Augmented Generation.
- Hiểu vai trò của Amazon Textract trong luồng xử lý tài liệu của hệ thống.
- Sử dụng Amazon Bedrock để tạo vector embedding từ nội dung văn bản.
- Lưu trữ vector embedding trong Amazon RDS PostgreSQL với `pgvector`.
- Xây dựng chức năng semantic search để tìm các đoạn tài liệu liên quan.
- Tạo dữ liệu thử nghiệm phục vụ kiểm tra hiệu năng Amazon RDS và Amazon DynamoDB.

### Nhật ký công việc

| Ngày | Công việc thực hiện | Kết quả | Nguồn tài liệu / Workshop |
|---|---|---|---|
| 27/07/2026 | Tìm hiểu Generative AI, Large Language Models và kiến trúc Retrieval-Augmented Generation (RAG). | Hiểu được luồng xử lý từ câu hỏi của người dùng, tạo embedding, truy xuất nội dung liên quan và sinh câu trả lời. | [Workshop 5.4.5.4 - Lambda Chatbot RAG](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.4-chatbot-rag/) |
| 28/07/2026 | Tìm hiểu Amazon Textract và vai trò của dịch vụ trong quá trình trích xuất nội dung tài liệu. | Hiểu cách nội dung tài liệu có thể được chuyển thành dữ liệu văn bản để tiếp tục xử lý trong pipeline RAG. | AWS Documentation - Amazon Textract |
| 29/07/2026 | Lựa chọn mô hình `amazon.titan-embed-text-v2:0` trên Amazon Bedrock để tạo vector embedding. | Xác định mô hình embedding của hệ thống với kích thước vector 1.024 chiều. | [Workshop 5.4.5.3 - Lambda tạo Vector Embedding](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.3-vector-lambda/) |
| 30/07/2026 | Xây dựng Lambda tạo vector embedding và lưu vector vào Amazon RDS PostgreSQL. | Văn bản được chuyển thành vector 1.024 chiều và lưu vào bảng `document_chunks`. | [Workshop 5.4.5.3 - Lambda tạo Vector Embedding](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.3-vector-lambda/) • [Workshop 5.4.5.2 - Lambda kết nối Amazon RDS](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.2-rds-lambda/) |
| 31/07/2026 | Xây dựng chức năng tìm kiếm vector trong PostgreSQL bằng cosine distance. | Có thể tìm các document chunk có vector gần nhất với vector truy vấn. | [Workshop 5.4.5.2 - Lambda kết nối Amazon RDS](/vi/5-workshop/5.4-backend-deployment/5.4.5-deploying-aws-lambda/5.4.5.2-rds-lambda/) |
| 01/08/2026 | Tạo và bơm 2.000 vector dữ liệu thử nghiệm vào Amazon RDS. | Có bộ dữ liệu đủ lớn để kiểm tra chức năng vector search và đo độ trễ truy vấn. | [Workshop 5.5 - Kiểm thử hệ thống](/vi/5-workshop/5.5-system-testing/) |
| 02/08/2026 | Tạo 100 phiên chat thử nghiệm, mỗi phiên gồm 20 tin nhắn trong Amazon DynamoDB. | Chuẩn bị dữ liệu phục vụ kiểm thử khả năng truy vấn lịch sử trò chuyện. | [Workshop 5.5 - Kiểm thử hệ thống](/vi/5-workshop/5.5-system-testing/) |

### Tổng kết tuần

- Hiểu được nguyên lý hoạt động của kiến trúc RAG.
- Lựa chọn và sử dụng Amazon Titan Text Embeddings V2 để tạo vector embedding.
- Hoàn thành luồng tạo và lưu vector 1.024 chiều vào Amazon RDS PostgreSQL.
- Xây dựng chức năng semantic search với `pgvector`.
- Chuẩn bị 2.000 vector thử nghiệm trên RDS.
- Chuẩn bị 100 phiên chat, mỗi phiên 20 tin nhắn trên DynamoDB.
- Hoàn thành dữ liệu đầu vào để tiến hành benchmark hiệu năng trong tuần tiếp theo.
