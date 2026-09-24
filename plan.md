# KẾ HOẠCH THỰC HIỆN ĐỀ TÀI C3
## NỀN TẢNG KIỂM THỬ HỢP ĐỒNG API VÀ MOCK SERVER
*(API Contract Testing and Mock Server Platform)*

### 1. Mục tiêu đề tài
*   Xây dựng một nền tảng hỗ trợ kiểm thử hợp đồng API dựa trên OpenAPI/Swagger và JSON Schema.
*   Cho phép người dùng import tài liệu OpenAPI, quản lý endpoint, request/response schema và status code.
*   Tự động chạy kiểm thử để kiểm tra API thực tế có đúng với hợp đồng đã định nghĩa hay không.
*   Xây dựng Mock Server để giả lập API trong trường hợp backend thật chưa hoàn thành.
*   Lưu lịch sử kiểm thử, hiển thị kết quả Passed/Failed và thống kê trên Dashboard.
*   Hỗ trợ phát hiện thay đổi API có nguy cơ gây lỗi cho hệ thống phía client.

### 2. Phạm vi chức năng chính
*   **Authentication và phân quyền:** Đăng ký, đăng nhập, đăng xuất, JWT, quản lý vai trò người dùng.
*   **Quản lý Project:** Tạo, sửa, xóa project; thêm thành viên; phân quyền trong project.
*   **Quản lý OpenAPI/Swagger:** Upload file YAML/JSON hoặc nhập Swagger URL; đọc danh sách endpoint, method, schema và status code.
*   **Contract Testing Engine:** Kiểm tra request, response, status code, header và JSON Schema.
*   **Test Runner:** Chạy một hoặc nhiều test case, lưu kết quả và hiển thị Passed/Failed.
*   **Mock Server:** Tạo endpoint giả, cấu hình response body, status code, header và delay.
*   **API Change Detection:** So sánh hai phiên bản API và cảnh báo breaking change.
*   **Dashboard và báo cáo:** Thống kê project, số API, số test, tỷ lệ pass/fail và lịch sử kiểm thử.

### 3. Công nghệ dự kiến
| Thành phần | Công nghệ |
| :--- | :--- |
| Frontend | React hoặc Next.js |
| Backend | Python FastAPI |
| Database | PostgreSQL |
| API Contract | OpenAPI/Swagger, JSON Schema |
| Testing | Pytest, HTTPX |
| Authentication | JWT |
| Container | Docker, Docker Compose |
| Quản lý mã nguồn | GitHub |
| CI/CD | GitHub Actions |

### 4. Phân chia nhiệm vụ cho 5 thành viên

**Thành viên 1 – Team Lead / Backend**
*   Quản lý tiến độ, GitHub, phân chia công việc và tích hợp chung.
*   Xây dựng Authentication: đăng ký, đăng nhập, đăng xuất, JWT.
*   Xây dựng User Management, Project Management, Project Member và phân quyền.
*   API chính: `/auth`, `/users`, `/projects`, `/projects/{id}/members`.
*   Phụ trách tài liệu: yêu cầu hệ thống, Use Case tổng quát, Project Plan.
*   Cuối dự án tổng hợp báo cáo và phối hợp demo.

**Thành viên 2 – OpenAPI / API Specification**
*   Nghiên cứu OpenAPI, Swagger và JSON Schema.
*   Xây dựng chức năng upload file `openapi.yaml` hoặc `openapi.json`.
*   Parse OpenAPI để lấy Method, Path, Parameters, Request Schema, Response Schema và Status Code.
*   Lưu thông tin API Specification và Endpoint vào cơ sở dữ liệu.
*   API chính: `/api-specs/upload`, `/api-specs`, `/api-specs/{id}/endpoints`.
*   Phụ trách tài liệu OpenAPI, thiết kế API Specification và Sequence Diagram liên quan.

**Thành viên 3 – Contract Testing Engine**
*   Xây dựng phần lõi Contract Testing.
*   Kiểm tra Request Schema, Response Schema, Status Code, Header và kiểu dữ liệu.
*   Xây dựng Test Case, Test Runner và Test Result.
*   Hiển thị nguyên nhân lỗi khi API thực tế không khớp hợp đồng.
*   API chính: `/tests`, `/tests/run`, `/tests/results`.
*   Phụ trách tài liệu Contract Testing, JSON Schema Validation và quy trình kiểm thử.

**Thành viên 4 – Mock Server**
*   Xây dựng Mock Server và quản lý Mock Endpoint.
*   Cho phép cấu hình Method, Path, Status Code, Response Body, Header và Delay.
*   Hỗ trợ Start/Stop Mock Server.
*   Cho phép giả lập các trường hợp 200, 400, 401, 404, 500.
*   Có thể bổ sung dữ liệu mẫu hoặc random data nếu còn thời gian.
*   Phụ trách tài liệu Mock Server, Activity Diagram và Sequence Diagram liên quan.

**Thành viên 5 – Frontend / Dashboard / DevOps**
*   Thiết kế giao diện Login, Dashboard, Project, API Specification, Endpoint, Contract Test, Test Result và Mock Server.
*   Kết nối Frontend với Backend API.
*   Hiển thị thống kê số project, API, test, Passed, Failed và tỷ lệ thành công.
*   Xây dựng Dockerfile và `docker-compose.yml`.
*   Thiết lập GitHub Actions cơ bản.
*   Phụ trách tài liệu UI, Deployment, Testing và hướng dẫn chạy hệ thống.

### 5. Cấu trúc cơ sở dữ liệu dự kiến
*   USERS
*   PROJECTS
*   PROJECT_MEMBERS
*   API_SPECS
*   API_ENDPOINTS
*   API_CONTRACTS
*   TEST_CASES
*   TEST_RUNS
*   TEST_RESULTS
*   MOCK_ENDPOINTS

### 6. Cấu trúc source code dự kiến
```text
api-contract-platform/
├── frontend/
├── backend/
├── contract-engine/
├── mock-server/
├── database/
├── docs/
├── docker-compose.yml
└── README.md
```

### 7. Kế hoạch thực hiện 10 tuần
| Thời gian | Công việc |
| :--- | :--- |
| Tuần 1 | Tìm hiểu REST API, OpenAPI, Swagger, JSON Schema, Contract Testing, Mock Server. Chốt phạm vi và yêu cầu. |
| Tuần 2 | Phân tích Functional/Non-functional Requirements, Actor, Use Case, luồng nghiệp vụ. |
| Tuần 3 | Thiết kế kiến trúc hệ thống, ERD, Database, API Design, Wireframe, Sequence Diagram và Activity Diagram. |
| Tuần 4 | Thành viên 1 làm Authentication, Project, Member; thành viên 5 làm Login, Dashboard và Project UI. |
| Tuần 5 | Thành viên 2 làm OpenAPI Import, Parser và API Endpoint Management; thành viên 5 làm giao diện API Specification. |
| Tuần 6 | Thành viên 3 làm Contract Testing Engine, Schema Validation, Test Runner và Test Result. |
| Tuần 7 | Thành viên 4 làm Mock Server, Dynamic Endpoint và Mock Response; thành viên 5 làm giao diện Mock Management. |
| Tuần 8 | Tích hợp Frontend, Backend, Contract Engine, Mock Server và Database. |
| Tuần 9 | Unit Test, Integration Test, API Test, System Test; Docker hóa và sửa lỗi. |
| Tuần 10 | Hoàn thiện báo cáo, slide, demo script, test report, source code và video demo. |

### 8. Phạm vi MVP bắt buộc
1. Authentication.
2. Project Management.
3. Import OpenAPI/Swagger.
4. Endpoint Management.
5. API Contract.
6. Contract Test Runner.
7. Schema Validation.
8. Test Result.
9. Mock Server.
10. Dashboard.

### 9. Chức năng nâng cao nếu còn thời gian
*   Breaking Change Detection.
*   CI/CD Integration.
*   Automatic Test Generation.
*   AI hỗ trợ sinh Test Case.
*   Test History Analytics.
*   Notification khi test thất bại.

### 10. Kịch bản demo cuối kỳ
11. Đăng nhập vào hệ thống.
12. Tạo một Project mới, ví dụ: E-Commerce API.
13. Import file `openapi.yaml`.
14. Hệ thống tự động đọc và hiển thị các endpoint.
15. Chạy Contract Test cho một endpoint hợp lệ và hiển thị PASS.
16. Cố tình thay đổi kiểu dữ liệu hoặc thiếu field để hệ thống hiển thị FAIL và nguyên nhân lỗi.
17. Tạo một Mock Endpoint cho API chưa có backend thật.
18. Gọi Mock API và nhận dữ liệu giả.
19. Mở Dashboard để xem tổng số API, số test, Passed, Failed và lịch sử chạy test.

### 11. Quy tắc làm việc nhóm
*   Mỗi thành viên làm trên branch riêng, không code trực tiếp vào main.
*   Mỗi chức năng hoàn thành phải tạo Pull Request để review trước khi merge.
*   Thống nhất API contract giữa frontend và backend trước khi code.
*   Cập nhật tiến độ tối thiểu 2 lần mỗi tuần.
*   Mỗi thành viên tự viết tài liệu cho phần mình phụ trách.
*   Trước khi demo phải có ít nhất một vòng integration test toàn hệ thống.

### 12. Tóm tắt phân công
| Thành viên | Vai trò | Phần chính |
| :--- | :--- | :--- |
| 1 | Team Lead / Backend | Authentication, User, Project, Member, phân quyền |
| 2 | OpenAPI Backend | Import Swagger/OpenAPI, Parser, Endpoint, Schema |
| 3 | Core Developer | Contract Testing Engine, Test Runner, Test Result |
| 4 | Mock Server Developer | Mock Endpoint, Mock Response, Status, Delay |
| 5 | Frontend / DevOps | UI, Dashboard, Docker, CI/CD, tích hợp |
