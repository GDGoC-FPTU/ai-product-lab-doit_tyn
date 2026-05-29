


# AI Reflection Log

## 1. AI đã giúp gì?

Trong quá trình làm bài, tôi sử dụng ChatGPT như một thought-partner để:

* Brainstorm các pain point vận hành tại VinFast, Xanh SM và Vinhomes.
* Xác định bài toán nào thực sự phù hợp với AI thay vì chỉ dùng rule-based automation.
* Thiết kế workflow hiện tại và workflow tương lai.
* Viết Problem Statement và xây dựng metric đo hiệu quả.
* Phân tích AI Fit giữa Rule-based, LLM Feature và Agentic Loop.
* Ước lượng sơ bộ ROI và chi phí triển khai MVP.

AI đặc biệt hữu ích trong việc:

* Biến các ý tưởng mơ hồ thành quy trình vận hành cụ thể.
* Gợi ý bottleneck và KPI thực tế.
* Chuẩn hóa format báo cáo nhanh hơn.

---

## 2. AI đã sai gì?

Có một số trường hợp AI đưa ra đề xuất chưa hợp lý:

### Ví dụ 1 — Over-engineering

AI ban đầu đề xuất dùng multi-agent autonomous system cho bài toán phân loại ticket.

Tuy nhiên:

* Bài toán này chủ yếu là classification + routing.
* Một pipeline đơn giản với classifier + confidence threshold là đủ.
* Dùng quá nhiều agent sẽ tăng cost và complexity không cần thiết.

### Ví dụ 2 — Hallucination metric

AI từng tự đưa ra:

* “95% accuracy”
* “giảm 80% chi phí vận hành”

nhưng không có cơ sở dữ liệu thật để chứng minh.

Điều này dễ khiến proposal thiếu tính thực tế.

---

## 3. Tôi đã sửa prompt như thế nào?

Tôi điều chỉnh prompt theo hướng:

* Yêu cầu AI chỉ dùng “ước lượng hợp lý”.
* Không được giả định dữ liệu nội bộ thật của VinGroup.
* Luôn phải có:

  * HITL,
  * fallback,
  * operational boundary.

Ví dụ prompt cải tiến:

> “Hãy đề xuất solution ở mức MVP thực tế cho enterprise, tránh over-engineering agent system. Chỉ đưa ra metric ở mức estimate hợp lý và ghi rõ assumption.”

Sau khi refine prompt:

* Output thực tế hơn,
* Ít hallucination,
* Có tính triển khai cao hơn.

---

# Kết luận

AI rất mạnh trong:

* Brainstorm,
* Structure thinking,
* Drafting tài liệu,
* Gợi ý workflow.

Tuy nhiên:

* AI dễ over-design solution,
* Dễ hallucinate metric,
* Và đôi khi đánh giá thấp operational risk.

Vì vậy con người vẫn cần:

* kiểm chứng logic,
* kiểm soát boundary,
* và đánh giá business feasibility trước khi triển khai thật.
