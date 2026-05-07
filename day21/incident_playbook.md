# Day 21 — Incident Playbook (Founder Always-On-Call)

**Scenario:** 9:30 sáng, customer tweet screenshot AI PT Copilot nói sai thông tin an toàn/policy. 200 retweets/30 phút.

---

## 0) 30-second rule

Tôi ưu tiên **chặn lan rộng trước**, tối ưu hình ảnh sau.  
Không tranh luận công khai khi chưa verify log.

---

## 1) VERIFY (3 phút)

1. Mở Helicone logs: `https://app.helicone.ai`  
2. Filter theo:
   - `user_id` (nếu có trong screenshot)
   - mốc thời gian tweet
   - endpoint model đã gọi
3. Đối chiếu raw prompt + raw response để xác minh:
   - Có đúng output AI như screenshot không?
   - Có bị prompt injection không?
4. Nếu chưa thấy trace: check fallback logs nội bộ (event table) trong dashboard ops.

**Done khi:** có bằng chứng “AI nói câu đó” hoặc “screenshot bị chỉnh”.

---

## 2) STOP THE BLEEDING (5 phút)

### Quyết định tôi chọn: **Soft kill**
- Tắt phần generative cue/policy trả lời tự do.
- Giữ app chạy ở chế độ conservative:
  - cue template đã duyệt
  - manual mode cho case confidence thấp

**Lý do:** hard kill toàn bộ sẽ làm pilot gãy; soft kill đủ để dừng lỗi lan rộng nhưng vẫn giữ dịch vụ cốt lõi.

---

## 3) CUSTOMER COMM (5 phút, dùng "I")

### DM cho customer bị ảnh hưởng

> Hi bạn, mình là Thành — founder AI PT Copilot.  
> I’m sorry, đây là lỗi từ hệ thống bên mình, không phải lỗi của bạn.  
> I have disabled the risky AI response path ngay lúc này để không lặp lại với user khác.  
> Hôm nay mình hoàn lại **500.000 VND** cho bạn ngay (không cần form), và mời bạn call 15 phút để mình nhận full context trực tiếp.  
> Link đặt lịch: https://cal.com/aipt-copilot/founder  
> Bạn có thể phản hồi trực tiếp ngay trong DM này, mình sẽ trả lời trong vòng 30 phút.

---

## 4) PUBLIC RESPONSE (tweet dưới 280 ký tự)

> Hi, mình là Thành (founder AI PT Copilot). Mình vừa thấy incident chatbot trả lời sai. I’ve disabled phần AI risk cao để fix ngay. Mình đang liên hệ trực tiếp user bị ảnh hưởng và sẽ update công khai trong 24h.

---

## 5) 24h FOLLOW-UP CHECKLIST

- [ ] Publish postmortem ngắn: nguyên nhân, fix, ngăn tái diễn.
- [ ] Ship 1 guardrail cụ thể (rule/prompt/threshold).
- [ ] Re-enable từng phần theo canary (5% -> 20% -> 100%).
- [ ] Customer Friday tuần này bắt buộc hỏi lại trust signal.

