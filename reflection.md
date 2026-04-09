# Báo Cáo Phản Tỉnh Cá Nhân (Reflection) - Hackathon

## 1. Role
**UI Lead (Phụ trách Giao diện người dùng)**. Tôi đảm nhận việc thiết kế luồng tương tác và triển khai mã nguồn phát triển Frontend cho dự án VinMec Lumina.

## 2. Đóng góp cụ thể
- **Triển khai Streamlit UI:** Viết lại toàn bộ giao diện từ HTML/CSS/JS thuần sang Streamlit để đáp ứng tiêu chí Minimum Viable Product (MVP), giúp đội Backend kết nối luồng xử lý bằng Python thuận tiện nhất.
- **Sidebar chọn bệnh nhân:** Xây dựng luồng chọn hồ sơ, tích hợp 3 file dữ liệu bệnh nhân mẫu (JSON) để Demo chức năng trơn tru.
- **Bảng kết quả xét nghiệm phân loại màu (Data Visualization):** Lập trình logic đối chiếu kết quả y khoa với khoảng tham chiếu (reference intervals), tự động bôi màu để cảnh báo (Xanh - Bình thường, Vàng - Theo dõi, Đỏ - Khẩn cấp).
- **Panel hiển thị AI Output:** Render các luồng nội dung của Langgraph, tách biệt rõ ràng phần tóm tắt, giải thích và đề xuất của AI để bệnh nhân dễ đọc.
- **Nút Feedback (Learning Signal):** Bố trí các nút tương tác đánh giá để thu lại phản hồi từ người dùng, làm dữ liệu tinh chỉnh cho AI sau này theo đúng định hướng ROI của dự án.

## 3. Đánh giá SPEC (Mạnh / Yếu)
- **Điểm mạnh:** SPEC của dự án được viết rất sắc nét, đặc biệt là phần **Clinical Safety Kill Switch** và phân loại các luồng lỗi (4 paths: Happy, Low-confidence, Failure, Correction). Điều này cho phép người làm giao diện (như tôi) có bộ quy tắc xử lý rõ ràng (ví dụ: khi Guardrails chặn kết quả nguy hiểm, UI sẽ bypass LLM và hiện thẳng màu đỏ mà không cần chờ). Tính năng tập trung cao độ, không bị lan man.
- **Điểm yếu:** SPEC định hướng thiên nhiều về báo cáo văn bản (text-generated output). Đối với người dùng phổ thông hoặc bệnh nhân lớn tuổi, đọc khối văn bản y khoa dù được tóm tắt vẫn gây áp lực. Đáng lẽ SPEC cần định nghĩa thêm hình thức báo cáo qua biểu đồ xu hướng (Trend graph layout) thay vì chỉ dùng text thuần.

## 4. Đóng góp khác
- **Đại diện bảo vệ dự án (System Defense):** Thay mặt nhóm thuyết trình về các luồng thao tác giao diện, giải thích về quyết định đánh đổi kiến trúc Web thuần lấy kiến trúc Streamlit để kịp tiến độ tích hợp (Working End-to-End).
- **Tham gia phản biện chéo (Cross-Review):** Tích cực tham gia Q&A, đặt câu hỏi phản biện về luồng dữ liệu, tính bảo mật và kỹ thuật của các sản phẩm nhóm khác, góp phần chuyên môn hóa không khí học thuật của buổi hackathon.

## 5. Điều học được
- **Tư duy Thực dụng (Pragmatic Engineering & Feasibility):** Tôi hiểu ra sức mạnh của sự linh hoạt (Agility). Chấp nhận bỏ qua giao diện cầu kỳ để lựa chọn một framework hiển thị theo hướng dữ liệu như Streamlit là bài học đắt giá về việc đánh đổi "cái tôi" lập trình lấy sự "về đích" của cả hệ thống.
- **Cách thấu hiểu sự khác biệt:** Nhờ việc góp ý và tranh luận chéo, tôi cải thiện kỹ năng biến các yếu tố kỹ thuật phức tạp thành lý luận ngôn ngữ đời thường, đồng thời học thêm những hướng tiếp cận mới từ các đội bạn.

## 6. Nếu làm lại
- **Kiến trúc luồng ngay từ đầu:** Tôi sẽ bỏ qua giai đoạn làm bản nháp tĩnh bằng HTML/CSS/JS (điều này khá lãng phí thời gian) và thiết lập mô hình Streamlit ngay từ ngày thứ nhất (Day 1) để dành toàn bộ khoảnh khắc quý giá làm các hiệu ứng animation hoặc biểu đồ đồ thị.
- **Sử dụng Session State bài bản hơn:** Tôi muốn đào sâu vào cơ chế State Management (Session State) của Streamlit để khắc phục hiện tượng load lại trang liên tục, giúp cho luồng UI tiệm cận hơn với một Single Page Application thực thụ.

## 7. AI giúp gì / AI sai gì
- **AI giúp gì:** AI (Copilot/ChatGPT) đã giúp tăng tốc độ coding đáng kể, đặc biệt là khi gen các boilerplate JSON (hồ sơ bệnh nhân giả lập), tự động hóa các hàm render bảng cấu trúc (Pandas vào Streamlit), và tối ưu logic phân tông màu cảnh báo y tế mà không cần ngồi viết tay từng lệnh `if/else`.
- **AI sai gì:** AI mắc lỗi "ảo giác" (hallucinate) trầm trọng khi cố gắng giải quyết sự không tương thích bất đồng bộ (async) giữa đồ thị LangGraph và cơ chế render của Streamlit. Code AI sinh ra thường đánh mất State hoặc gọi lại Agent nhiểu lần, buộc tôi phải tự can thiệp kiểm tra lại tài liệu (Docs) và tự refactor cấu trúc quản lý luồng bằng tay.
