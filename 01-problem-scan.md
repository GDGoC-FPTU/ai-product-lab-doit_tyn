# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

### 📝 List bài toán của tôi:

| # | Subsidiary | Lens             | Mô tả ngắn bài toán                                                                                                                     |
| - | ---------- | ---------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | VinFast    | Repetitive       | Nhân viên CSKH phải phân loại hàng nghìn ticket lỗi xe mỗi ngày (pin, OTA, động cơ, app) rồi route thủ công sang đúng bộ phận kỹ thuật. |
| 2 | Xanh SM    | Stakeholder Pain | Tài xế phàn nàn hệ thống gợi ý điểm đón chưa chính xác tại khu đông người (TTTM, bệnh viện), dẫn tới hủy chuyến cao.                    |
| 3 | Vinhomes   | Time-consuming   | Nhân viên vận hành mất nhiều thời gian đọc và phản hồi review/complaint 1-star từ cư dân trên app cư dân và Facebook.                   |
| 4 | Vinmec     | AI-upgrade       | Call center đặt lịch khám còn phụ thuộc người trực tổng đài, thời gian chờ cao giờ cao điểm.                                            |
| 5 | Vinpearl   | AI-upgrade       | Chatbot hỗ trợ đặt phòng/vé vui chơi trả lời rập khuôn, không cá nhân hóa theo nhóm khách gia đình/cặp đôi/doanh nghiệp.                |
| 6 | VinFast    | Time-consuming   | Bộ phận bảo hành phải đọc ảnh/video khách gửi để xác minh lỗi ngoại thất trước khi approve sửa chữa.                                    |
| 7 | Xanh SM    | Repetitive       | Điều phối viên phải xử lý thủ công các case tài xế bị mất kết nối GPS hoặc route bất thường.                                            |
| 8 | Vinhomes   | Stakeholder Pain | Cư dân phàn nàn việc xử lý ticket kỹ thuật (điện nước/thang máy) chậm do ticket thiếu thông tin mô tả ban đầu.                          |

---

# 🃏 Phase 2 — QUICK-ASSESS

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                      │
│                                                             │
│ Bài toán: Phân loại và route ticket lỗi xe tự động cho     │
│ hệ thống CSKH VinFast                                      │
│                                                             │
│ Công ty thành viên: [x] VinFast                            │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ - Nhân viên CSKH                                           │
│ - Đội kỹ thuật hậu mãi                                     │
│                                                             │
│ Workflow thủ công hiện tại:                                │
│   1. Khách gửi ticket lỗi                                  │
│      ──> 2. CSKH đọc mô tả                                 │
│      ──> 3. Chọn nhóm lỗi thủ công                         │
│      ──> 4. Route sang kỹ thuật phù hợp                    │
│      ──> 5. Theo dõi phản hồi                              │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ - Bước phân loại lỗi và route ticket                       │
│ - ⏱ ~6–8 phút/ticket                                       │
│ - Sai route ~12–15% ticket                                 │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ - NLP/LLM tự động đọc mô tả lỗi                            │
│ - Predict nhóm lỗi                                         │
│ - Auto-routing sang đúng team kỹ thuật                     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm thời gian xử lý từ 8 phút → dưới 1 phút/ticket      │
│ - Giảm tỷ lệ route sai từ 15% → dưới 3%                    │
│ - Giảm backlog ticket 40%                                  │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [ ] Rule  [x] LLM  [x] Agent                    │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                      │
│                                                             │
│ Bài toán: Tự động phản hồi complaint cư dân Vinhomes       │
│ theo ngữ cảnh và mức độ ưu tiên                            │
│                                                             │
│ Công ty thành viên: [x] Vinhomes                           │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ - Nhân viên chăm sóc cư dân                                │
│ - Ban quản lý tòa nhà                                      │
│                                                             │
│ Workflow thủ công hiện tại:                                │
│   1. Cư dân gửi complaint                                  │
│      ──> 2. Nhân viên đọc nội dung                         │
│      ──> 3. Xác định mức độ nghiêm trọng                   │
│      ──> 4. Soạn phản hồi                                  │
│      ──> 5. Chuyển ticket cho vận hành                     │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ - Soạn phản hồi và phân loại urgency                       │
│ - ⏱ ~10–15 phút/case                                       │
│ - Dễ phản hồi thiếu cảm xúc hoặc sai tone                  │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ - Sentiment analysis                                       │
│ - AI draft phản hồi theo tone chuyên nghiệp                │
│ - Auto-prioritize ticket                                   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm thời gian phản hồi từ 15 phút → dưới 2 phút         │
│ - Tăng CSAT từ 3.8 → 4.5/5                                 │
│ - Giảm complaint escalation 30%                            │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent                    │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                      │
│                                                             │
│ Bài toán: Tối ưu điểm đón khách cho tài xế Xanh SM         │
│ tại khu vực đông người                                     │
│                                                             │
│ Công ty thành viên: [x] Xanh SM                            │
│                                                             │
│ Ai đang đau (Actor)?                                       │
│ - Tài xế Xanh SM                                           │
│ - Khách hàng đặt xe                                        │
│                                                             │
│ Workflow thủ công hiện tại:                                │
│   1. Khách đặt xe                                          │
│      ──> 2. Hệ thống chọn điểm đón mặc định                │
│      ──> 3. Tài xế gọi xác nhận                            │
│      ──> 4. Khách mô tả lại vị trí                         │
│      ──> 5. Tài xế tìm khách                               │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất?                           │
│ - Tìm đúng điểm đón thực tế                                │
│ - ⏱ Mất thêm ~5–7 phút/chuyến giờ cao điểm                │
│ - Tăng tỷ lệ hủy chuyến                                    │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                      │
│ - Predict pickup hotspot theo lịch sử                      │
│ - Computer vision/map intelligence                         │
│ - Gợi ý dynamic pickup point                               │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                      │
│ - Giảm thời gian đón khách từ 7 phút → dưới 3 phút         │
│ - Giảm tỷ lệ hủy chuyến 20%                                │
│ - Tăng completed trip/hour thêm 15%                        │
│                                                             │
│ Quick Architecture:                                        │
│ [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent                    │
└─────────────────────────────────────────────────────────────┘
