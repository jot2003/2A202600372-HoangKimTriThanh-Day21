# Day 21 — Risk Register (3 risks, runway-based)

**Startup:** AI PT Copilot  
**Monthly burn rate (ước tính):** ~**200.000.000 VND/tháng**  
**Runway conversion:**  
- 200M VND mất = 1 tháng runway  
- 600M VND mất = 3 tháng runway  
- 1,2B VND mất = 6 tháng runway

---

## Risk #1 — Vendor Risk (LLM policy / outage)

**If** OpenAI thay đổi policy hoặc rate-limit làm summary/cue fallback không hoạt động ổn định trong giờ cao điểm,  
**Then** user nhận phản hồi chậm/sai ngữ cảnh trong 1-2 tuần,  
**Leading to** churn tăng và mất khoảng **3 tháng runway** vì phải chạy hotfix + giữ chân + chậm pilot.

- **Likelihood:** 4  
- **Impact:** 4 (3-6 tháng runway)  
- **Score:** **16** → **KILL ZONE**

---

## Risk #2 — Customer-facing AI Risk (Air Canada style)

**If** chatbot/cue trả lời sai policy an toàn hoặc pricing cho user mới,  
**Then** user chụp màn hình đăng mạng xã hội, case viral + yêu cầu hoàn tiền,  
**Leading to** brand damage và mất khoảng **2 tháng runway** do support + refunds + đóng băng tăng trưởng.

- **Likelihood:** 3  
- **Impact:** 2 (1-2 tháng runway)  
- **Score:** 6

---

## Risk #3 — Founder-bandwidth Risk (single point of failure)

**If** tôi bị ốm 3-5 ngày đúng lúc có incident production,  
**Then** team không có người quyết định stop-the-bleeding đủ nhanh,  
**Leading to** sự cố kéo dài thành khủng hoảng và mất khoảng **4 tháng runway**.

- **Likelihood:** 3  
- **Impact:** 4 (3-6 tháng runway)  
- **Score:** 12

---

## Priority order

1. **Risk #1 (Score 16, KILL ZONE)** — xử lý trước trong playbook.  
2. Risk #3 (Score 12).  
3. Risk #2 (Score 6).

