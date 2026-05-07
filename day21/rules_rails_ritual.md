# Day 21 — Rules / Rails / Ritual (AI PT Copilot)

**Founder:** Hoàng Kim Trí Thành  
**Risk lớn nhất tôi chọn:** AI coach đưa cue sai policy/an toàn trong phiên tập đầu, user mất niềm tin và sự cố bị viral.

---

## R1 — RULES (1 trang, founder-led)

**Last updated:** 07/05/2026  
**Owner update:** Founder cập nhật trực tiếp tại Notion: `notion.so/aiptcopilot/ai-safety-rules`

### ❌ KHÔNG được làm
- KHÔNG paste chat user / dữ liệu sức khỏe / video tập vào ChatGPT public hoặc Claude public.
- KHÔNG deploy prompt/rule mới cho cue an toàn nếu chưa có pre-launch review của founder.
- KHÔNG trả lời customer policy bằng AI tự do; chỉ dùng policy snippets đã duyệt.

### ✅ Được làm (alternative có vendor + cost)
- Dùng **OpenAI Team** cho nội bộ (data không dùng train theo workspace controls), ~**$30/user/tháng**.
- Dùng **Cursor + GitHub PR review** cho coding workflow, ~**$20/user/tháng**.
- Dùng **Helicone** để log prompt/response và trace incident, gói free giai đoạn đầu (**$0/tháng**).

### ⚠️ Hậu quả vi phạm
- Lần 1: Tôi gọi 1:1 trong ngày + ghi note hành động khắc phục.
- Lần 2: Dừng quyền truy cập production ngay + chấm dứt hợp tác.

---

## R2 — RAILS (stack dưới $500/tháng, triển khai 1 tuần)

| Mục tiêu chặn rủi ro | Tool / Vendor | Cost ước tính |
|---|---|---:|
| Chặn secrets/API keys trong git | `gitleaks` + pre-commit hook | $0 |
| LLM logging + incident trace | Helicone | $0 (free tier) |
| Prompt/rule change phải qua review | GitHub branch protection + required reviewer | $0 |
| Chặn paste data nhạy cảm ra ngoài | NextDNS policy block domain public LLM | ~$20/tháng |
| Workspace LLM có quyền quản trị | OpenAI Team (5 users x $30) | ~$150/tháng |

**Total rails cost:** ~**$170/tháng** (< $500/tháng).

---

## R3 — RITUAL (weekly, founder-operable)

### Friday 30' AI Safety Check (mỗi thứ 6)
- 10': review 5 prompt/cue lỗi nhiều nhất tuần (từ Helicone).
- 10': chọn 1 root-cause fix sẽ ship tuần sau.
- 10': kiểm tra 1 customer complaint và phản hồi trực tiếp.

### Customer Friday question (cụ thể)
> "Trong buổi tập tuần này, có cue nào bạn thấy sai hoặc làm bạn mất niềm tin ngay lập tức không? Câu đó là gì?"

Tôi dùng đúng 1 câu này mỗi tuần để bắt tín hiệu trust collapse sớm, thay vì hỏi chung "trải nghiệm ổn không?".

---

## 1-week implementation plan

- Day 1: bật Helicone + branch protection + gitleaks.
- Day 2: viết rules trong Notion + team read & acknowledge.
- Day 3-4: cấu hình NextDNS blocklist + test false positives.
- Day 5: chạy Customer Friday lần đầu, ghi action item tuần kế tiếp.

