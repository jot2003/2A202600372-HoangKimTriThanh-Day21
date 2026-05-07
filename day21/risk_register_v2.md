# Day 21 — Risk Register v2 (AI-augmented, 10+ risks)

**Context:** merge từ Workshop 2 + AI CRO prompt round 1-2  
**Burn rate quy đổi:** 200.000.000 VND/tháng  
**Mục tiêu:** tìm KILL ZONE sớm, chọn mitigation founder-implementable (<$500/tháng)

---

## 1) Comprehensive risk list (12 risks, cover 5 types)

| # | Type | Risk statement (If-Then-Leading to) | L | I | Score |
|---|---|---|---:|---:|---:|
| 1 | Vendor | If OpenAI policy/rate-limit đổi đột ngột, then summary/cue fallback lỗi, leading to mất 3 tháng runway | 4 | 4 | **16** |
| 2 | Vendor | If app store policy camera/privacy đổi, then release bị reject 2-4 tuần, leading to mất 2 tháng runway | 3 | 3 | 9 |
| 3 | Vendor | If cloud logging vendor outage, then incident verify chậm, leading to mất 1 tháng runway | 3 | 2 | 6 |
| 4 | Customer-facing | If AI cue sai policy/an toàn bị viral, then refund + trust drop, leading to mất 2 tháng runway | 3 | 2 | 6 |
| 5 | Customer-facing | If onboarding camera setup fail trên máy phổ thông, then drop-off tuần đầu tăng, leading to mất 2 tháng runway | 4 | 2 | 8 |
| 6 | Founder-bandwidth | If founder ốm 3-5 ngày khi có incident, then quyết định chậm, leading to mất 4 tháng runway | 3 | 4 | 12 |
| 7 | Founder-bandwidth | If founder ôm cả product + CS + safety review, then burnout và quality giảm, leading to mất 3 tháng runway | 4 | 3 | 12 |
| 8 | Reputational | If prompt injection screenshot lan truyền, then báo chí/community gắn nhãn “AI bịa”, leading to mất 3 tháng runway | 3 | 4 | 12 |
| 9 | Reputational | If founder phản hồi kiểu corporate “we are investigating”, then user thấy né trách nhiệm, leading to mất 1 tháng runway | 3 | 2 | 6 |
|10 | Regulatory | If xử lý dữ liệu sức khỏe thiếu consent rõ ràng, then bị khiếu nại/tuýt còi, leading to mất 5 tháng runway | 2 | 5 | 10 |
|11 | Regulatory | If retention policy data không rõ xóa dữ liệu, then không ký được partnership gym/doanh nghiệp, leading to mất 2 tháng runway | 3 | 3 | 9 |
|12 | Customer-facing | If false cue ở 2 session đầu không được chặn, then trust collapse, leading to mất 3 tháng runway | 4 | 3 | 12 |

> **5 types covered:** Vendor / Customer-facing / Founder-bandwidth / Reputational / Regulatory.

---

## 2) AI-found risks I missed initially (evidence)

### AI-found #1 — Founder communication risk (Risk #9)
- **Tôi miss vì:** tôi chỉ nghĩ rủi ro kỹ thuật, chưa nghĩ “tone phản hồi” cũng là risk.
- **AI chỉ ra:** phản hồi corporate làm mất trust nhanh trong startup nhỏ.
- **Tôi học được:** founder voice là control surface, không phải cosmetic.

### AI-found #2 — Data retention / deletion compliance risk (Risk #11)
- **Tôi miss vì:** assume “startup nhỏ chưa bị soi”.
- **AI chỉ ra:** thiếu chính sách xóa dữ liệu làm fail B2B partnerships trước cả khi bị phạt.
- **Tôi học được:** regulatory risk không chỉ là fine; còn là revenue blocker.

### AI-found #3 — Logging vendor outage as incident multiplier (Risk #3)
- **Tôi miss vì:** nghĩ logging chỉ là observability phụ.
- **AI chỉ ra:** khi mất trace, verify chậm -> crisis time tăng theo cấp số nhân.
- **Tôi học được:** logging là survival tool trong giờ đầu.

---

## 3) Top 5 KILL ZONE / near-KILL risks + 3 mitigation options

## Risk A — #1 OpenAI policy/rate-limit shock (Score 16)

**Option 1:** Multi-vendor abstraction (OpenAI + Anthropic)  
- Cost: ~$80/tháng infra + ops  
- Pros: failover nhanh  
- Cons: thêm complexity

**Option 2:** Template summary fallback local  
- Cost: $0-$20/tháng  
- Pros: deploy trong 1-2 ngày  
- Cons: chất lượng summary giảm

**Option 3:** Rate-limit budget guard + queue  
- Cost: ~$30/tháng  
- Pros: giảm spike failures  
- Cons: vẫn phụ thuộc vendor

**Chosen:** Option 1 + 2 (failover + fallback) vì triển khai <7 ngày và giữ continuity tốt nhất.

---

## Risk B — #6 Founder unavailable during incident (Score 12)

**Option 1:** Incident deputy rotation (1 engineer + 1 PM backup)  
- Cost: $0 direct (chỉ process)  
- Pros: giảm single point of failure  
- Cons: cần training hàng tuần

**Option 2:** 1-page runbook + canned comm templates  
- Cost: $0  
- Pros: pass 3-AM test  
- Cons: cần discipline update

**Option 3:** External on-call advisor retained  
- Cost: ~$300-$500/tháng  
- Pros: thêm lớp kinh nghiệm  
- Cons: cost tăng

**Chosen:** Option 1 + 2 ngay; Option 3 chỉ bật khi scale > 500 MAU pilot.

---

## Risk C — #8 Prompt injection viral reputational hit (Score 12)

**Option 1:** Strict allowlist cho policy-related responses  
- Cost: ~$0-$50/tháng  
- Pros: giảm surface area  
- Cons: bớt linh hoạt

**Option 2:** Real-time anomaly alert từ logging  
- Cost: ~$30/tháng  
- Pros: phát hiện sớm 15-30 phút  
- Cons: cần tuning

**Option 3:** Pre-approved founder tweet templates  
- Cost: $0  
- Pros: phản hồi nhanh, giữ trust  
- Cons: phải luyện trước

**Chosen:** Option 1 + 2 + 3 (combo low-cost, triển khai trong tuần).

---

## Risk D — #12 Trust collapse early sessions (Score 12)

**Option 1:** Conservative mode cho 2 session đầu  
- Cost: $0 dev config  
- Pros: giảm false cue sớm  
- Cons: feedback ít hơn

**Option 2:** Confidence threshold cá nhân hoá theo user  
- Cost: ~$100/tháng compute+logging  
- Pros: quality tăng theo thời gian  
- Cons: cần telemetry sạch

**Option 3:** Manual “report wrong cue” 1-tap  
- Cost: $0-$20/tháng  
- Pros: thu signal nhanh  
- Cons: phụ thuộc user feedback

**Chosen:** Option 1 + 3 ngay; Option 2 triển khai sau 2 tuần pilot.

---

## Risk E — #10 Consent/compliance failure (Score 10, regulatory)

**Option 1:** Consent flow bắt buộc + delete-data self-service  
- Cost: $0-$50/tháng  
- Pros: giảm legal exposure mạnh  
- Cons: thêm 1 bước onboarding

**Option 2:** Quarterly legal review ngoài  
- Cost: ~$300-$500/tháng (fractional)  
- Pros: cập nhật luật nhanh  
- Cons: tốn chi phí

**Option 3:** Internal checklist release gate (privacy-by-default)  
- Cost: $0  
- Pros: rẻ, triển khai nhanh  
- Cons: phụ thuộc kỷ luật team

**Chosen:** Option 1 + 3 ngay; Option 2 khi ký partnership B2B đầu tiên.

---

## 4) Founder action plan (2 tuần tới)

- Tuần 1: ship multi-vendor fallback + deputy rotation + consent/delete flow.
- Tuần 2: bật anomaly alerts + conservative mode session 1-2 + wrong-cue feedback.
- Mỗi thứ 6: review top-5 risks lại theo score, cập nhật risk register.

