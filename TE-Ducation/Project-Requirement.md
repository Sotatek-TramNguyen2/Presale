Dựa trên tài liệu Proposal dự án TE-Ducation và các tài liệu kiến trúc của hệ thống SotaAgent, dưới đây là chi tiết về các chức năng, giao diện của giai đoạn POC và các thông tin BA cần chuẩn bị để khởi tạo (init) ứng dụng này.

## 1. Các Function (Chức năng) trong POC WBS
Giai đoạn POC tập trung vào việc xác thực khả năng chấm điểm tự động của AI, do đó WBS bao gồm 5 module chức năng chính:

## 2. Các màn hình (Screens) trong POC
POC **không phải là một cổng thông tin (portal)** có tính năng đăng nhập phức tạp cho học sinh hay phụ huynh.

## 3. Các Input BA cần có để "init" 1 app TE-Ducation
Dựa vào luồng khởi tạo CLI (`sota init`) của nền tảng và các yêu cầu chuẩn bị (Assumptions) trong Proposal, BA sẽ cần chốt các input sau để có thể khởi tạo chính xác bộ khung ứng dụng:

### A. Thông tin kỹ thuật & Lệnh CLI khởi tạo

### B. Dữ liệu Nghiệp vụ (Core Business Inputs)
Để app POC thực sự chạy được với AI Sota Agents, BA cần làm việc với khách hàng (TE-Ducation) để thu thập trước khi bắt đầu code:
