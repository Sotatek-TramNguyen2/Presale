Sample HTML: https://drive.google.com/drive/folders/1BKcl85eVsXVa7EDrfnlJ7nNQvDRqEx_i
Sample test: https://drive.google.com/drive/folders/1gnMVXGAukbd0Ns4aR0xwhSoGgT1b9YJ9

Dựa trên tài liệu Proposal dự án TE-Ducation và các tài liệu kiến trúc của hệ thống SotaAgent, dưới đây là chi tiết về các chức năng, giao diện của giai đoạn POC và các thông tin BA cần chuẩn bị để khởi tạo (init) ứng dụng này.

### 1. Các Function (Chức năng) trong POC WBS

Giai đoạn POC tập trung vào việc xác thực khả năng chấm điểm tự động của AI, do đó WBS bao gồm 5 module chức năng chính:

- **MOD-001: Tiếp nhận bài nộp (Submission Intake):** Form cho phép dán nội dung bài luận, nhập tên/ID học sinh, chọn loại môn học (như Tiếng Anh, Lịch sử, Học bổng) và có các API backend đi kèm để xử lý.
- **MOD-002: Chọn Barem (Rubric Selection):** Giao diện danh sách chọn 1-2 barem (rubric) đã được tải sẵn lên Knowledge Base của Sota Agents và gắn barem đó vào payload chấm điểm.
- **MOD-003: Động cơ chấm điểm AI (Sota Agents Grading Engine):**

- Cấu hình AI Research Agent và thiết kế prompt theo cấu trúc rubric.
- Phân tích cấu trúc đầu ra: điểm số, điểm chữ, xếp loại (band), phân tích điểm thành phần, danh sách Điểm mạnh/Điểm cần cải thiện, và gợi ý bước tiếp theo.
- Hiển thị trạng thái theo thời gian thực (đang phân tích → hoàn thành), tính năng "Yêu cầu AI chấm lại" (Ask AI to Regrade) và xử lý lỗi/timeout.
- **MOD-004: Báo cáo kết quả (Result Report):** Hiển thị chi tiết kết quả trả về từ AI, cùng với một danh sách tổng hợp nhiều bài chấm mẫu (multi-sample list) kèm cột Điểm AI và Trạng thái AI.
- **MOD-005: Lưu trữ POC (POC Storage):** Thiết lập cơ sở dữ liệu và các API lưu/trích xuất các bản ghi như bài nộp, kết quả của Sota Agents, timestamp.

### 2. Các màn hình (Screens) trong POC

POC **không phải là một cổng thông tin (portal)** có tính năng đăng nhập phức tạp cho học sinh hay phụ huynh.

- Về mặt UI, nó là một **Single-page web interface (Giao diện web một trang)** chỉ dành cho quản trị viên hoặc gia sư (Admin/Tutor).
- Toàn bộ luồng thao tác từ việc dán bài nộp, chọn rubric, xem tiến độ chấm điểm, hiển thị kết quả phân tích và danh sách các bài đã chấm sẽ nằm trên các khu vực (panel) của trang duy nhất này.

### 3. Các Input BA cần có để "init" 1 app TE-Ducation

Dựa vào luồng khởi tạo CLI (`sota init`) của nền tảng và các yêu cầu chuẩn bị (Assumptions) trong Proposal, BA sẽ cần chốt các input sau để có thể khởi tạo chính xác bộ khung ứng dụng:

**A. Thông tin kỹ thuật & Lệnh CLI khởi tạo**

- **Tên App ID:** Cần định danh một ID hợp lệ (ví dụ: `te-ducation-poc`), viết thường không dấu.
- **Cờ kiến trúc (Cần Backend hay không?):** BA phải xác nhận chạy lệnh **`sota init te-ducation-poc --service`**. Lý do là vì WBS của POC có chứa MOD-001 và MOD-005 yêu cầu phải có cơ sở dữ liệu (PostgreSQL) và backend API endpoint riêng, nên không thể chỉ dùng bộ khung tĩnh.
- **Môi trường Origin & Token:** Thông tin máy chủ Sandbox/Staging và Operator Secret từ SotaTek để trỏ CLI tới đúng hệ thống.
- **Cấu hình Giao diện (Manifest):** Vì màn hình POC dành cho Admin/Tutor thao tác trên một tool nội bộ, BA cần chỉ định UI này sẽ đóng góp dưới dạng **`kind: frame`** (giao diện quản trị/console) thay vì `artifactSlot` (giao diện làm việc trực tiếp của Agent).

**B. Dữ liệu Nghiệp vụ (Core Business Inputs)**
Để app POC thực sự chạy được với AI Sota Agents, BA cần làm việc với khách hàng (TE-Ducation) để thu thập trước khi bắt đầu code:

- **Chốt 1 loại hình đánh giá đầu tiên (First assessment type):** Cần xác định ngay POC sẽ test môn nào trước (ví dụ: Bài luận Tiếng Anh, hoặc Viết học bổng) để làm nền tảng cấu hình prompt template.
- **1-2 Barem mẫu (Rubrics):** TE-Ducation phải cung cấp/duyệt trước 1-2 barem thực tế định dạng file PDF/DOCX để nạp vào hệ thống Knowledge Base (RAG).
- **Dữ liệu mẫu (Sample Essays):** Tối thiểu **10 bài luận mẫu của học sinh đã được gia sư chấm điểm thực tế** cho mỗi barem để nhóm AI dùng làm căn cứ căn chỉnh (calibration) prompt trước khi bàn giao.
