# 📊 BÁO CÁO THU HOẠCH NGHIỆM THU BÀI LAB 3 (BƯỚC 3 — SUBMISSION ARTIFACT)

> **Họ và Tên Học viên:** Đàm Quang Sơn  
> **Mã Sinh Viên / Mã Học viên:** 2A202602868  
> **Chủ đề Lựa chọn:** Trợ lý Học vụ Sinh viên VinUni  

---

## 1. BẢNG CHẤM ĐIỂM AGENTIC FIT SCORING MATRIX (ĐÁNH GIÁ CHỦ ĐỀ)

| Tiêu chí Đánh giá | Mức độ (1 - 5) | Giải trình chi tiết lý do chọn điểm |
| :--- | :---: | :--- |
| **1. Multi-step Reasoning** | 4 / 5 | Một số yêu cầu cần chia thành nhiều bước, ví dụ tra cứu hồ sơ để biết cố vấn rồi mới đặt lịch đúng người phụ trách. |
| **2. Tool Interaction** | 5 / 5 | Hệ thống cần gọi MCP Server để tra cứu dữ liệu sinh viên và thực hiện hành động đặt lịch, không thể chỉ trả lời bằng kiến thức chung. |
| **3. Dynamic Decision** | 4 / 5 | Agent phải quyết định trả lời trực tiếp, gọi `academic_query`, gọi `schedule_appointment`, hoặc xử lý `NOT_FOUND` tùy nội dung câu hỏi và Observation. |
| **4. Long Horizon Goal** | 3 / 5 | Mục tiêu chính là hỗ trợ học vụ trong một phiên ngắn; vẫn cần giữ ngữ cảnh thao tác qua các bước Thought -> Action -> Observation. |
| **TỔNG ĐIỂM AGENTIC FIT** | **16 / 20** | Bài toán phù hợp triển khai Agentic System vì tổng điểm > 12/20 và có nhu cầu dùng công cụ rõ ràng. |

---

## 2. TRÍCH XUẤT KẾT QUẢ WATERFALL TRACE LOG (SAU KHI CHẠY TEST SUITE TRÊN API THẬT)

> ⚠️ **YÊU CẦU NGHIỆM THU:** Mở tệp `.env` điền `GEMINI_API_KEY` (hoặc `OPENAI_API_KEY`) để kết nối LLM thật trước khi thực thi `python src/app.py --all`. Bài nộp chỉ dùng Mock Offline Provider sẽ không đạt điểm nghiệm thực tế.

Dán 1 đoạn trích xuất log tiêu biểu từ file `docs/trace_waterfall.json` sinh ra từ phản hồi LLM API thật:

```json
[
  {
    "step": 1,
    "query": "Hãy tra cứu cố vấn học tập của sinh viên SV2026002 rồi đặt lịch tư vấn cho bạn ấy vào 15:30 16/09/2026.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "academic_query",
    "arguments": {
      "student_id": "SV2026002"
    },
    "observation": {
      "status": "SUCCESS",
      "student_id": "SV2026002",
      "data": {
        "full_name": "Trần Thị Bình",
        "class": "AI-K4",
        "gpa": 3.6,
        "email": "binh.tt@vinuni.edu.vn",
        "status": "Đang học",
        "advisor": "TS. Lê Thị B"
      }
    },
    "latency_ms": 0.0
  },
  {
    "step": 2,
    "query": "Hãy tra cứu cố vấn học tập của sinh viên SV2026002 rồi đặt lịch tư vấn cho bạn ấy vào 15:30 16/09/2026.",
    "action_type": "TOOL_EXECUTION",
    "tool_name": "schedule_appointment",
    "arguments": {
      "student_id": "SV2026002",
      "datetime_str": "15:30 16/09/2026",
      "advisor_name": "TS. Lê Thị B"
    },
    "observation": {
      "status": "SUCCESS",
      "booking_id": "BK-SV2026002-99",
      "student_id": "SV2026002",
      "datetime": "15:30 16/09/2026",
      "advisor": "TS. Lê Thị B",
      "message": "Đặt lịch thành công cho sinh viên SV2026002 với TS. Lê Thị B vào lúc 15:30 16/09/2026."
    },
    "latency_ms": 10.0
  }
]
```

---

## 3. TỔNG KẾT KẾT QUẢ NGHIỆM THU & NỘP BÀI

- [x] Đã điền API Key thật trong `.env` và xác nhận Agent chạy mượt mà trên LLM API thật (Gemini).
- **Tổng số Test Cases đã chạy thành công:** 5 / 5 test cases trên Gemini API thật.
- **Số lượt gọi Tool qua MCP Server chính xác:** 5 lượt trên Gemini API thật.
- **Kết quả đẩy Repo nộp bài:** [ ] Cần học viên Commit và Push mã nguồn lên GitHub cá nhân.

---

> ✅ **HOÀN TẤT NỘP BÀI:** Sao chép đường link GitHub Repository cá nhân của bạn và dán vào ô nộp bài trên hệ thống LMS VLearn để hoàn tất Bài Lab 3!
