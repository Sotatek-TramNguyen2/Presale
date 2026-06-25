# Project-Requirement.md

### 1\. Các Function (Chức năng) trong POC WBS

* **MOD-001: Tiếp nhận bài nộp (Submission Intake):** Form nhập nội dung bài luận/thuyết trình, ID học sinh, chọn loại môn học.
* **MOD-002: Chọn Barem (Rubric Selection):** Danh sách chọn barem đã tải sẵn trên Knowledge Base.
* **MOD-003: Động cơ AI và Nhúng dữ liệu (AI Engine \& Embedding):** AI phân tích điểm, xếp loại (VD: Band 4-6) và cấu trúc bài. **Thuật toán nhúng sâu ngầm (Background Embedding) toàn bộ Khung chương trình NESA và tiêu chuẩn đánh giá của Úc**.
* **MOD-004: Báo cáo kết quả chấm (Grading Report):** Báo cáo chi tiết trả về từ AI (Scorecard, Criteria breakdown, Actionable feedback).
* **MOD-005: Tạo bài mẫu chuẩn (Exemplar Generation):** **AI tự động tạo bài luận mẫu đạt chuẩn Band 6 dựa trên đề thi cũ bằng cơ chế One-click button**.
* **MOD-006: Tự động hóa nhận xét học bạ (Personalized Comments):** **Hệ thống phân tích kết quả bài kiểm tra/thuyết trình để tự động xuất nhận xét cá nhân hóa bằng tiếng Anh học thuật chuẩn**.
* **MOD-007: Lưu trữ \& Bảo mật (Storage \& Security):** **Lưu trữ CSDL (PostgreSQL) và áp dụng các tiêu chuẩn bảo mật nghiêm ngặt nhất của giáo dục Úc khi xử lý dữ liệu học sinh**.

### 2\. Các màn hình (Screens) trong POC

* **Giao diện web một trang (Single-page web interface):** Dành riêng cho Admin/Tutor thao tác nội bộ.
* **Màn hình Dashboard Chấm điểm \& Báo cáo:** Tích hợp form nộp bài, chọn rubric, xem tiến độ và hiển thị kết quả (Interactive Highlight Map, Score Ring, phản hồi).
* **Màn hình Sinh bài mẫu Band 6:** Giao diện cho phép nhập đề thi cũ và xuất ra bài luận mẫu Band 6 kèm phân tích kỹ thuật.
* **Xử lý ngầm (No UI - Background Processing):**

  * **Thuật toán nhúng Khung chương trình (Syllabus outcomes) và học máy định nghĩa "Excellence" trong văn phong học thuật**.
  * **Hệ thống bảo mật dữ liệu học sinh và lưu trữ Database API (PostgreSQL)**.
  * **Luồng xử lý tự động hóa nhận xét học bạ cá nhân hóa từ kết quả thô của học sinh**.

### 3\. Các Input BA cần có để "init" 1 app TE-Ducation

**A. Thông vị kỹ thuật \& Lệnh CLI khởi tạo**

* **Tên App ID:** `te-ducation-poc`.
* **Cờ kiến trúc (Cần Backend):** Bắt buộc chạy lệnh **`sota init te-ducation-poc --service`** để tạo backend và database.
* **Cấu hình Môi trường:** Trỏ Origin bằng lệnh **`sota config set-origin <url>`** và thiết lập **`sota config set operatorSecret <token>`**.
* **Cấu hình Giao diện (Manifest):** Khai báo **`kind: frame`** (giao diện quản trị/console) thay vì artifactSlot.

**B. Dữ liệu Nghiệp vụ (Core Business Inputs)**

* **Chốt 1 loại hình đánh giá (First assessment type):** Chọn 1 môn học duy nhất (VD: Advanced English) để cấu trúc POC trước khi nhân rộng ra 565 trường.
* **Barem mẫu (Rubrics) \& Tiêu chuẩn:** Khách hàng cung cấp 1-2 barem thực tế định dạng PDF/DOCX và tài liệu Syllabus outcomes.
* **Dữ liệu mẫu (Sample Essays):** Tối thiểu **10 bài luận mẫu (từ Band thấp đến Band 6)** đã được gia sư chấm thực tế để làm căn cứ AI calibration.

