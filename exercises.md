# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> Khi temperature thấp như 0.0, câu trả lời thường ổn định, trực tiếp và ít biến thiên giữa các lần gọi. Khi tăng lên 0.5, 1.0 và 1.5, mô hình có xu hướng đa dạng và sáng tạo hơn, nhưng cũng dễ thêm chi tiết ít chắc chắn hoặc diễn đạt lan man hơn.

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Tôi sẽ đặt khoảng 0.2-0.4 cho chatbot hỗ trợ khách hàng. Mức này giúp câu trả lời nhất quán, dễ kiểm soát và giảm nguy cơ bịa thông tin, nhưng vẫn đủ tự nhiên để không quá máy móc.

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> Workload là 10.000 x 3 x 350 = 10.500.000 token mỗi ngày. Theo bảng giá trong `template.py`, GPT-4o đắt hơn GPT-4o-mini khoảng 33,3 lần cho cả input token (5.00 / 0.150) và output token (20.00 / 0.600), nên tỷ lệ tổng chi phí cũng xấp xỉ 33,3 lần.

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> GPT-4o xứng đáng khi tác vụ cần lập luận tốt, độ chính xác cao hoặc xử lý tình huống phức tạp, ví dụ phân tích hồ sơ khách hàng quan trọng, soạn phản hồi pháp lý sơ bộ hoặc kiểm tra lỗi logic trong tài liệu dài. GPT-4o-mini phù hợp hơn cho tác vụ khối lượng lớn và rủi ro thấp như phân loại ticket, tóm tắt ngắn, gợi ý câu trả lời nháp hoặc FAQ tự động.

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng cần cảm giác hệ thống đang xử lý ngay, ví dụ chatbot hội thoại, trợ lý viết nội dung, giải thích từng bước hoặc tạo báo cáo dài. Việc hiển thị từng phần giúp giảm cảm giác chờ và cho phép người dùng đọc sớm trước khi toàn bộ câu trả lời hoàn tất. Non-streaming phù hợp hơn khi cần một kết quả hoàn chỉnh để xử lý tiếp bằng code, ghi log, chấm điểm, parse JSON hoặc đảm bảo UI chỉ cập nhật khi phản hồi đã hợp lệ toàn bộ.


## Danh Sách Kiểm Tra Nộp Bài
- [x] Tất cả tests pass: `pytest tests/ -v`
- [x] `call_openai` đã triển khai và kiểm thử
- [x] `call_openai_mini` đã triển khai và kiểm thử
- [x] `compare_models` đã triển khai và kiểm thử
- [x] `streaming_chatbot` đã triển khai và kiểm thử
- [x] `retry_with_backoff` đã triển khai và kiểm thử
- [x] `batch_compare` đã triển khai và kiểm thử
- [x] `format_comparison_table` đã triển khai và kiểm thử
- [x] `exercises.md` đã điền đầy đủ
- [x] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
