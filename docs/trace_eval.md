# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Nguyễn Hồng Phi
> **Mã Sinh Viên / Mã Học viên:** 2A202602750  
> **Chủ đề Lựa chọn:** Trợ lý Học vụ & Tra cứu Lịch thi VinUni (chủ đề 1.1)  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | TC04 yêu cầu Agent phân rã mục tiêu thành chuỗi `academic_query` để lấy cố vấn rồi `schedule_appointment`; ngoài ra vẫn có các yêu cầu đơn bước. |
| **2. Tool Interaction** | 5 / 5 | Agent phải gọi MCP Server để tra hồ sơ học vụ và thực hiện thao tác đặt lịch, thay vì chỉ trả lời từ kiến thức có sẵn. |
| **3. Dynamic Decision** | 5 / 5 | Agent phải đọc Observation, lấy đúng `advisor` từ hồ sơ sinh viên và dùng giá trị đó làm tham số cho bước đặt lịch; mã không hợp lệ cũng làm thay đổi nhánh trả lời sang `NOT_FOUND`. |
| **4. Long Horizon Goal** | 3 / 5 | Một số mục tiêu kéo dài qua hai lượt gọi tool và cần duy trì ngữ cảnh; tuy nhiên chưa có quy trình dài hạn, bộ nhớ bền vững hoặc theo dõi nhiều phiên. |
| **TỔNG ĐIỂM AGENTIC FIT** | **17 / 20** | Tổng điểm cao, phù hợp triển khai ReAct Agent vì có tool interaction, quyết định động và chuỗi xử lý nhiều bước rõ ràng. |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG

> ⚠️ Khi nghiệm thu chính thức, cần cấu hình API key của provider đang chọn (hiện tại là `OPENROUTER_API_KEY`) trong `.env` và chạy lại test suite.

Dưới đây là trích đoạn thực tế từ `docs/trace_waterfall.json` (TC02):

```json
[
  {
    "step": 1,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026001"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026001",
      "data": {
        "full_name": "Nguyễn Văn An",
        "class": "AI-K4",
        "gpa": 3.85,
        "advisor": "PGS.TS Nguyễn Văn A"
      }
    },
    "latency_ms": 0.0
  },
  {
    "step": 2,
    "query": "Hãy tra cứu thông tin học vụ của sinh viên SV2026001.",
    "action_type": "FINAL_ANSWER",
    "output": "Kết quả tra cứu cho sinh viên SV2026001 (Nguyễn Văn An): Lớp AI-K4, GPA: 3.85, Email: an.nv@vinuni.edu.vn, Trạng thái: Đang học, Cố vấn: PGS.TS Nguyễn Văn A.",
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (OpenRouter).
- **Tổng số Test Cases đã thực thi:** **5 / 5 test cases**.
- **Số lượt gọi Tool qua MCP Server:** **5 lượt**.
- **Kết quả theo hành vi kỳ vọng:** **TC01–TC05 đạt**; TC04 thực hiện chuỗi `academic_query → schedule_appointment`, TC05 trả về `NOT_FOUND` cho `SV9999999`.
- **Kết quả đẩy Repo nộp bài:** [ ] Đã Commit và Push mã nguồn thành công lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
