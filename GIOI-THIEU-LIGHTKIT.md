# Lightkit — Khi AI build phần mềm, ai quyết định cái gì?

Bạn mở Claude, gõ "build cho tôi app quản lý kho", AI viết code. Xong. Nhưng rồi bạn nhận ra: tính năng không đúng ý, authentication thiếu, workflow sai logic, và khi sửa thì không biết lỗi từ đâu — từ yêu cầu mơ hồ, từ AI tự ý thêm feature, hay từ code chạy sai spec.

Đây không phải lỗi của AI. Đây là lỗi của việc không có quy trình.

Lightkit giải quyết vấn đề này. Nó không phải bộ prompt để AI code giỏi hơn — mà là một **phương pháp vận hành** quy định rõ: ai quyết định cái gì, bằng quy trình nào, và kiểm chứng ra sao.

---

## 3 vai trò, ranh giới cứng

Framework chia workflow thành 3 vai trò với ranh giới không được phép vi phạm:

**Chủ nhà (Con người)** ra quyết định chiến lược — chọn tính năng nào cần, duyệt kiến trúc, approve scope. Chủ nhà không code, không thiết kế chi tiết.

**Chủ thầu (AI thiết kế)** phỏng vấn yêu cầu, lên bản vẽ, chia task, kiểm tra chất lượng. Chủ thầu không viết dòng code nào.

**Thợ thi công (AI code)** nhận task có spec rõ ràng, code đúng spec, tự test, nộp báo cáo. Thợ không được sáng tạo, không được tự thêm feature, không được tự quyết khi gặp mâu thuẫn.

Nguyên tắc "Thợ không được phép sáng tạo" nghe khắc nghiệt nhưng đánh thẳng vào lỗi phổ biến nhất khi dùng AI build phần mềm: scope drift. Khi AI vừa thiết kế vừa code, nó có xu hướng tự bổ sung tính năng, tự đổi kiến trúc, tự quyết những thứ lẽ ra bạn nên quyết. Tách vai trò ra giải quyết triệt để vấn đề này.

---

## RRI — Phỏng vấn ngược thay vì hỏi "bạn muốn gì?"

Phần khác biệt nhất của Lightkit không nằm ở code generation mà ở requirements discovery.

Hầu hết workflow AI hiện tại bắt đầu bằng: bạn mô tả ý tưởng → AI code luôn. Vấn đề là phần mô tả thường thiếu 60-70% thông tin cần thiết — bạn quên nói về error handling, về edge cases, về ai có quyền làm gì, về deploy ở đâu.

RRI (Reverse Requirements Interview) đảo ngược flow: thay vì hỏi "bạn muốn gì?", AI đề xuất trước — "Tôi đề xuất JWT auth với refresh token, đồng ý không?" — rồi bạn duyệt hoặc bác.

Cơ chế hoạt động qua 3 lớp:

- **AUTO-ANSWERED**: Nếu đã scan codebase, những gì code cho thấy rõ thì không hỏi lại. Giảm ~30% câu hỏi thừa.
- **CHALLENGE**: AI đề xuất pattern phổ biến, bạn chỉ cần yes/no. Nhanh, nén được ~40% câu hỏi xuống dạng xác nhận.
- **EXPLORE**: Chỉ những chỗ thật sự chưa rõ mới hỏi mở. Khoảng 30% câu hỏi còn lại.

Mỗi câu hỏi được hỏi từ góc nhìn của 1 trong 5 persona: End User, Business Analyst, QA/Tester, Developer, Operator. Kết quả là 40-60 câu hỏi thông minh trong 30-45 phút thay vì 100+ câu hỏi mệt mỏi hay zero câu hỏi rồi code sai.

Output của RRI là một Requirements Matrix — mỗi yêu cầu có REQ-ID, priority, và persona gốc. REQ-ID này theo suốt vòng đời dự án.

---

## 8 bước, khép kín và truy vết được

```
SCAN → RRI → VISION → BLUEPRINT → TASK GRAPH → BUILD → VERIFY → REFINE
```

**SCAN** — Thợ scan codebase (hoặc xác nhận folder trống), báo cáo tech stack, patterns, gaps.

**RRI** — Chủ thầu phỏng vấn ngược, sinh Requirements Matrix.

**VISION** — Chủ thầu phân tích project qua 6 chiều (Interface, Data flow, User model, Lifecycle, Scale, State), đề xuất kiến trúc + tech stack.

**BLUEPRINT** — Bản vẽ chi tiết: cấu trúc, design system, file structure, mapping REQ-IDs. Chủ nhà duyệt "APPROVED" thì mới đi tiếp.

**TASK GRAPH** — Chủ thầu chia Blueprint thành các TIP (Task Instruction Pack) có dependency map. Mỗi TIP có: context, spec, acceptance criteria dạng Gherkin, constraints.

**BUILD** — Thợ nhận TIP, code đúng spec, tự test theo acceptance criteria, nộp Completion Report ghi rõ: status, files changed, test results, issues discovered, deviations.

**VERIFY** — Chủ thầu kiểm tra ngược: mỗi REQ-ID đã được implement chưa? Coverage bao nhiêu %? Test pass bao nhiêu?

**REFINE** — Fix issues từ Verify, nhưng chỉ trong phạm vi đã approved. Muốn thêm feature mới? Quay lại VISION.

Điều quan trọng: mỗi artifact trỏ về artifact trước nó. REQ-004 sinh từ RRI câu #15 → được mapping vào Blueprint section 3 → được implement trong TIP-004 → acceptance criteria tested trong Completion Report → verified trong Verify Report. Khi có bug, bạn trace được đến tận quyết định gốc.

---

## Ví dụ nhanh

Bạn nói: "Chủ thầu, tôi cần API quản lý đơn hàng, Python FastAPI."

Chủ thầu scan folder trống, chạy RRI: "Bao nhiêu loại user? Workflow đơn hàng có mấy bước? Cần payment integration không? Deploy đâu?" — 45 câu qua 5 personas.

Kết quả RRI: 23 REQ-IDs, 8 quyết định đã chốt. Chủ thầu đề xuất Vision, lập Blueprint chi tiết, bạn duyệt.

Chủ thầu sinh 6 TIPs: Scaffold → DB → API → Auth → Test → Deploy. Gửi từng TIP cho Thợ.

Thợ code TIP-001, nộp Completion Report: "DONE, 12 files, 3/3 AC passed." Chủ thầu review, gửi TIP-002.

Sau 6 TIPs, Chủ thầu chạy Verify: "Coverage 100%, 14/15 scenarios passed, 1 minor issue." Bạn quyết định ship.

Bạn chỉ ra 3 quyết định chiến lược. AI xử lý phần còn lại — nhưng có kiểm soát, có truy vết, có báo cáo.

---

## 4 protocol đặc biệt

Ngoài workflow chính, Lightkit có 4 protocol dùng độc lập:

**Debug Protocol** — Khi fix nhanh fail 3 lần liên tiếp, tự động chuyển sang quy trình gỡ lỗi 9 bước: thu thập bằng chứng → lập giả thuyết → kiểm chứng từng cái → fix 1 thứ một lúc. Nguyên tắc: không bao giờ đoán mò.

**QA Protocol** — Nghiệm thu 3 tầng. Tier 1 (bắt buộc): core functionality + acceptance criteria. Tier 2 (khuyến nghị): edge cases + responsive. Tier 3 (tùy chọn): performance + security. Mỗi test case trỏ về REQ-ID.

**X-Ray Protocol** — Chụp X-quang codebase cho bàn giao, onboarding, hoặc đánh giá technical debt. Output: PROJECT_XRAY.md với kiến trúc, dependency map, code health, và traceability từ feature → requirement → code.

**RRI mở rộng** — RRI-T (Testing: 5 Personas × 7 Dimensions × 8 Stress Axes), RRI-UX (UX Critique: 5 UX Personas × 7 UX Dimensions × 8 Flow Physics), RRI-UI (kết hợp cả hai).

---

## Lightkit không phải gì

Không phải code generator — framework không viết code, nó quản lý quy trình để AI viết code đúng.

Không phải bộ template cho web app — v6 là general-purpose, dùng cho web, mobile, CLI, API, data pipeline, hay bất kỳ loại phần mềm nào.

Không phải locked vào Claude — methodology là agent-agnostic, bất kỳ AI nào có thể plan thì làm Contractor, AI nào code được thì làm Builder. Implementation hiện tại map vào Claude Chat + Claude Code.

Không phải magic — framework không thay thế việc bạn hiểu domain và ra quyết định. Nó chỉ đảm bảo quyết định của bạn được truyền đạt chính xác, implement đúng, và kiểm chứng được.

---

## Bắt đầu

Cài file `lightkit.skill` vào Claude, mở chat, gõ:

> "Chủ thầu, tôi muốn build [mô tả dự án của bạn]."

Framework sẽ tự kích hoạt và dẫn bạn qua từng bước.

Lightkit v6.0 — by Khangkk.
