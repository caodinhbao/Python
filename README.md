# API Contract Testing and Mock Server Platform

Nền tảng hỗ trợ kiểm thử hợp đồng API (API Contract Testing) dựa trên OpenAPI/Swagger và cung cấp Mock Server để giả lập API.

## Cấu trúc dự án
- `frontend/`: Giao diện người dùng (React / Next.js)
- `backend/`: API quản lý nền tảng (Python FastAPI)
- `contract-engine/`: Lõi kiểm thử hợp đồng API (Pytest, HTTPX)
- `mock-server/`: Máy chủ giả lập API
- `database/`: Scripts và cấu hình cơ sở dữ liệu (PostgreSQL)
- `docs/`: Tài liệu dự án

## Khởi động
Dự án có thể chạy bằng Docker Compose:
```bash
docker-compose up -d
```
