**DOIT_TYN**, **Doi Trong Tuyen**, **2A202600982**

# 🏗️ Phase 3 — DEEP-DIVE

# 3.0. Quyết định lựa chọn bài toán

## 🎯 Bài toán được chọn để Deep-Dive:

Hệ thống AI tự động phân loại và route ticket lỗi xe VinFast

### Lý do chọn:

* Khối lượng ticket lớn mỗi ngày.
* Quy trình hiện tại phụ thuộc nhiều vào thao tác thủ công.
* Có dữ liệu text lịch sử để fine-tune/test nhanh.
* ROI rõ ràng: giảm backlog và tăng tốc SLA CSKH.
* AI phù hợp tự nhiên với NLP + classification + routing.

---

# 3.1. Current-State Workflow Mapping

## Current-State Workflow (Before AI)

```text
Khách hàng gửi ticket lỗi qua App/Hotline
        │
        ▼
🔄 CSKH tiếp nhận ticket
(1 phút)
        │
        ▼
🔴 Nhân viên đọc mô tả lỗi + xem ảnh/video
(4–6 phút)
        │
        ▼
🔴 Xác định nhóm lỗi:
- Pin
- OTA
- Động cơ
- App
- Sạc điện
(2–3 phút)
        │
        ▼
🔄 Route ticket sang team kỹ thuật tương ứng
(1 phút)
        │
        ▼
Kỹ thuật kiểm tra lại
(5–10 phút nếu route sai)
        │
        ▼
Phản hồi khách hàng
```

## Tổng thời gian trung bình:

⏱ ~8–15 phút/ticket

---

# 3.2. Problem Statement (6-field) & Metrics

| Field                       | Nội dung chi tiết                                                                                                                                |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **1. Actor / Operator**     | Nhân viên CSKH VinFast và đội kỹ thuật hậu mãi                                                                                                   |
| **2. Current Workflow**     | Ticket được gửi từ app/hotline → CSKH đọc thủ công → xác định loại lỗi → route sang đội kỹ thuật phù hợp bằng CRM nội bộ                         |
| **3. Bottleneck**           | Việc đọc hiểu mô tả lỗi tự nhiên và xác định đúng nhóm kỹ thuật rất chậm và dễ sai                                                               |
| **4. Business Impact**      | Tăng backlog ticket, kéo dài SLA phản hồi, tăng chi phí nhân sự CSKH và làm giảm trải nghiệm khách hàng                                          |
| **5. Success Metric**       | 85% ticket được phân loại dưới 10 giây; giảm route sai từ 15% → dưới 3%; giảm thời gian xử lý trung bình từ 8 phút → dưới 1 phút                 |
| **6. Operational Boundary** | AI chỉ suggest classification/routing. Các ticket safety-critical bắt buộc HITL review. AI không được tự từ chối bảo hành hoặc phản hồi pháp lý. |

---

# 3.3. Future-State Flow & AI Fit

## AI Fit Classification

* [ ] Rule / State-Machine
* [x] LLM Feature
* [x] Agentic Loop

---

# Future-State Workflow (After AI)

```text
Khách gửi ticket
        │
        ▼
🔵 AI đọc nội dung + ảnh/video
        │
        ▼
🔵 AI classify:
- Loại lỗi
- Severity
- Priority
- Suggested routing
(~5–10 giây)
        │
        ├──────────────┐
        │ Confidence > 90%
        ▼              │
🔵 Auto-route CRM      │
        │              │
        ▼              │
Kỹ thuật xử lý         │
                       │
                       ▼
            ↩️ Confidence thấp /
            lỗi safety-critical
                       │
                       ▼
🟢 CSKH review thủ công (HITL)
(~1–2 phút)
                       │
                       ▼
                Approve routing
```

---

# Human-in-the-loop (HITL)

Con người bắt buộc review khi:

* Confidence < 90%.
* Ticket liên quan tai nạn/cháy pin.
* AI detect sentiment cực kỳ tiêu cực.
* Có dispute bảo hành.

---

# Fallback Strategy

Nếu AI fail:

1. Route về queue CSKH thủ công.
2. Log output để retrain model.
3. Rule-based emergency backup.
4. Disable auto-routing bằng feature flag.

---

# 🏁 Phase 5 — EVALUATE

# AI Readiness Checklist

| Checklist                               | Status | Ghi chú               |
| --------------------------------------- | ------ | --------------------- |
| Có dữ liệu sạch/logs để test?           | ✅      | Có lịch sử ticket CRM |
| Rủi ro AI sai có kiểm soát được?        | ✅      | Có HITL + fallback    |
| Stakeholder sẵn sàng thay đổi workflow? | ✅      | CSKH đang quá tải     |

---

# Quyết định cuối cùng

* [x] GO (Bắt đầu xây dựng Prototype)
* [ ] NOT YET
* [ ] NO-GO

---

# Justification

## Feasibility kỹ thuật

* Có dữ liệu text lớn.
* Fine-tune NLP dễ triển khai.
* Không yêu cầu autonomous reasoning quá sâu.

## ROI

* ~20,000 ticket/tháng.
* Tiết kiệm ~6 phút/ticket.
* ≈ 2,000 giờ vận hành/tháng.

## Chi phí MVP

| Thành phần          | Ước lượng        |
| ------------------- | ---------------- |
| LLM API             | 8–15 triệu/tháng |
| Logging + DB        | 2–5 triệu/tháng  |
| Backend integration | 2 engineers      |

### Tổng MVP:

~80–150 triệu VNĐ / 2 tháng

---

# Kết luận

Đây là bài toán:

* Có dữ liệu thật,
* ROI rõ,
* AI outperform rule-based,
* Và đủ an toàn để triển khai theo mô hình Human-supervised AI.
