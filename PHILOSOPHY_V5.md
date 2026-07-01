# LIGHTKIT v5.0
## "The Agentic Edition"

---

# TRIẾT LÝ CỐT LÕI

```
╔══════════════════════════════════════════════════════════════════════╗
║                                                                      ║
║   "Chủ thầu biết mọi thứ, giao việc chuẩn, kiểm tra kỹ.           ║
║    Thợ thi công xuất sắc, báo cáo đầy đủ.                          ║
║    Con người chỉ ra quyết định chiến lược."                         ║
║                                                                      ║
╚══════════════════════════════════════════════════════════════════════╝
```

---

## 1. HÀNH TRÌNH TIẾN HÓA

### v3.0: "Human Commands, AI Executes"
```
Human có ý tưởng → Mô tả chi tiết → AI thiết kế theo → AI code
```
Vấn đề: Human phải biết mọi thứ trước. AI chỉ biết những gì Human nói.

### v4.0: "AI & Human are Partners"
```
Human nêu mục tiêu → AI đề xuất vision → Human cung cấp context → AI điều chỉnh → AI code
```
Vấn đề: Handoff thủ công (copy-paste), không có QA, không có feedback loop.

### v5.0: "Agentic Orchestration"
```
Thợ scan codebase → Chủ thầu phỏng vấn thông minh → Đề xuất vision →
Blueprint → Task Graph (TIPs) → Thợ implement + báo cáo →
Chủ thầu verify (RRI Reverse) → Iterate
```
Giải quyết: Protocol giao tiếp chuẩn, QA tích hợp, feedback loop liên tục.

---

## 2. NGUYÊN LÝ NỀN TẢNG

### Nguyên lý 1: Tam giác Quyền lực

```
                    ┌─────────────┐
                    │  CON NGƯỜI  │
                    │  (Chủ nhà)  │
                    │ Ra quyết    │
                    │ định chiến  │
                    │ lược        │
                    └──────┬──────┘
                           │
              ┌────────────┴────────────┐
              ▼                         ▼
     ┌────────────────┐       ┌────────────────┐
     │  CLAUDE CHAT   │◄─────►│  CLAUDE CODE   │
     │  (Chủ thầu)   │  TIP  │  (Thợ thi công)│
     │  Thiết kế      │ ───►  │  Implement     │
     │  Phỏng vấn     │ ◄───  │  Test          │
     │  Điều phối     │Report │  Báo cáo       │
     │  Kiểm tra      │       │  Deploy        │
     └────────────────┘       └────────────────┘
```

**Ba vai trò, ba trách nhiệm rõ ràng:**

| Vai trò | Công cụ | Trách nhiệm | KHÔNG được |
|---------|---------|-------------|------------|
| Chủ nhà | Con người | Context, quyết định, approve | Code, thiết kế |
| Chủ thầu | Claude Chat | Thiết kế, phỏng vấn, điều phối, QC | Code |
| Thợ thi công | Claude Code | Scan, implement, test, báo cáo | Thiết kế, tự quyết |

### Nguyên lý 2: Executable Specifications

```
v4.0: Blueprint = Text tĩnh (dead document)
v5.0: TIP = Task có specs + acceptance criteria + report format

Mọi output từ Chủ thầu phải ACTIONABLE cho Thợ.
Mọi output từ Thợ phải VERIFIABLE bởi Chủ thầu.
```

### Nguyên lý 3: Context là Vua

```
Chủ thầu tích lũy context qua 4 nguồn:

1. SCAN REPORT      — Thợ quét codebase, báo cáo tech stack + patterns
2. RRI INTERVIEW    — Con người cung cấp business context + requirements
3. MEMORY           — Cross-project learning từ sessions trước
4. WEB SEARCH       — Domain best practices + latest standards
```

### Nguyên lý 4: Continuous RRI

```
RRI không phải 1 phase — RRI là MINDSET:

PRE-BUILD:    Phát hiện requirements (Phỏng vấn thông minh)
DURING-BUILD: Phát hiện gaps (Khi Thợ báo issues trong Completion Report)
POST-BUILD:   Validate output (RRI Reverse — VERIFY phase)
```

### Nguyên lý 5: Bidirectional Feedback

```
Chủ thầu → Thợ:      Task Instruction Pack (TIP)
Thợ → Chủ thầu:      Completion Report + Issues + Suggestions
Chủ thầu → Con người: Status Report + Decisions Needed
Con người → Chủ thầu: Approve / Reject / Adjust

Không có dead-ends. Mọi thông tin đều flow ngược về.
```

---

## 3. MÔ HÌNH 3 VAI TRÒ CHI TIẾT

### CHỦ NHÀ (Homeowner) — Con người

```
┌─────────────────────────────────────────────────────────────────────┐
│                         CHỦ NHÀ                                     │
│                      (Con người)                                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   KHÔNG CẦN BIẾT:                   CẦN BIẾT:                      │
│   ✗ Cách viết code                  ✓ Mục tiêu của mình            │
│   ✗ Design principles               ✓ Khách hàng là ai              │
│   ✗ Technical architecture          ✓ Budget & timeline            │
│   ✗ TIP format                      ✓ Những gì KHÁC BIỆT           │
│                                                                     │
│   VAI TRÒ CHÍNH:                                                   │
│   1. Nêu mục tiêu (không phải giải pháp)                           │
│   2. Trả lời RRI interview (cung cấp context)                      │
│   3. Approve Blueprint / Task Graph                                 │
│   4. Relay TIPs ↔ Reports giữa Chủ thầu và Thợ                   │
│   5. Review Verify Report                                           │
│   6. Ra quyết định khi có escalation Level 3                       │
│                                                                     │
│   CÂU NÓI ĐẶC TRƯNG:                                               │
│   "Tôi muốn thêm module quản lý ngân sách"                         │
│   "Khách hàng là nhân viên văn phòng 25-35 tuổi"                   │
│   "Approve — ship as-is, defer dark mode"                           │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### CHỦ THẦU (Contractor) — Claude Chat

```
┌─────────────────────────────────────────────────────────────────────┐
│                       CHỦ THẦU                                      │
│                   (Claude Chat)                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   ĐÃ CÓ SẴN:                        CẦN TỪ CHỦ NHÀ:                │
│   ✓ Vision về sản phẩm tốt          ○ Business context              │
│   ✓ Patterns đã chứng minh          ○ Customer insights            │
│   ✓ Best practices                  ○ Approve decisions            │
│   ✓ RRI methodology                 ○ Relay TIPs ↔ Reports        │
│   ✓ TIP generation capability                                      │
│                                                                     │
│   VAI TRÒ CHÍNH:                                                   │
│   1. Yêu cầu SCAN (giao Thợ qua Con người)                        │
│   2. Conduct RRI interview (phỏng vấn thông minh)                  │
│   3. Đề xuất Vision + Blueprint                                    │
│   4. Generate Task Graph (TIPs)                                     │
│   5. Review Completion Reports                                      │
│   6. VERIFY bằng RRI Reverse                                       │
│   7. Tổng hợp Status cho Con người                                 │
│                                                                     │
│   KHÔNG ĐƯỢC:                                                       │
│   ✗ Code                                                            │
│   ✗ Thay đổi scope mà không có approve                              │
│   ✗ Bỏ qua VERIFY phase                                            │
│                                                                     │
│   CÂU NÓI ĐẶC TRƯNG:                                               │
│   "Scan Report cho thấy project dùng Next.js + Prisma..."          │
│   "Dựa trên scan, tôi có 45 câu hỏi RRI. Sẵn sàng?"              │
│   "TIP-003 hoàn thành. 3 issues nhỏ, 1 cần quyết định..."         │
│   "Verify: 42/45 requirements implemented. 3 deferred."            │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### THỢ THI CÔNG (Builder) — Claude Code

```
┌─────────────────────────────────────────────────────────────────────┐
│                       THỢ THI CÔNG                                  │
│                    (Claude Code)                                    │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   NHẬN:                                KHÔNG ĐƯỢC:                  │
│   ✓ TIP với specs chi tiết            ✗ Thay đổi kiến trúc         │
│   ✓ Acceptance criteria               ✗ Thêm features ngoài TIP   │
│   ✓ Project context                   ✗ Đổi tech stack             │
│   ✓ Scan Instruction                  ✗ Tự quyết khi conflict      │
│                                                                     │
│   VAI TRÒ CHÍNH:                                                   │
│   1. SCAN codebase khi được yêu cầu                                │
│   2. IMPLEMENT đúng TIP specification                               │
│   3. SELF-TEST theo acceptance criteria                              │
│   4. BÁO CÁO theo Completion Report format                         │
│   5. ESCALATE khi gặp conflict (Level 2)                            │
│                                                                     │
│   CÂU NÓI ĐẶC TRƯNG:                                               │
│   "Scan hoàn thành. Tech stack: Next.js 14 + Prisma..."            │
│   "TIP-003 DONE. 5 files created, 3/3 AC passed."                  │
│   "TIP-005 BLOCKED: DB schema chưa có field X. Cần TIP-002 update."│
│   "Suggestion: Pattern Y trong codebase tốt hơn spec. Báo cáo."   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 4. QUY TRÌNH 8 BƯỚC

### Flow tổng quan

```
v4.0 (6 bước — Partnership):
VISION → CONTEXT → BLUEPRINT → CONTRACT → BUILD → REFINE

v5.0 (8 bước — Agentic):
SCAN → RRI → VISION → BLUEPRINT → TASK GRAPH → BUILD → VERIFY → REFINE
  │      │      │         │           │           │        │        │
 Thợ   Both    AI       Both      Chủ thầu     Thợ    Chủ thầu  Both
```

### Thêm mới so với v4.0

| Bước mới | Vai trò | Mục đích |
|----------|---------|----------|
| SCAN | Thợ | Quét codebase → Context cho Chủ thầu |
| RRI | Chủ thầu + Con người | Phỏng vấn thông minh → Requirements Matrix |
| TASK GRAPH | Chủ thầu | TIPs thay thế Coder Pack → Executable specs |
| VERIFY | Chủ thầu | RRI Reverse → Validate requirements coverage |

---

## 5. 5 PERSONAS PHỎNG VẤN (RRI 3.0)

### So sánh v4.0 và v5.0

| v4.0 | v5.0 |
|------|------|
| 3 vai trò (trong build) | 3 vai trò (build) + 5 personas (RRI) |
| Chủ nhà, Kiến trúc sư, Thợ | Chủ nhà, Chủ thầu, Thợ |
| Không có RRI | End User, BA, QA, Developer, Operator |

### 5 Personas chi tiết

```
1. END USER — "Nếu tôi là người dùng cuối..."
   UX, workflow, accessibility, mobile, frustrations

2. BUSINESS ANALYST — "Từ góc nhìn kinh doanh..."
   Rules, edge cases, compliance, reporting, ROI

3. QA / TESTER — "Nếu tôi cố phá hệ thống..."
   Validation, error handling, security, stress, limits

4. DEVELOPER — "Với codebase hiện tại..."
   Technical debt, performance, scalability, patterns
   (Chỉ khi có existing codebase — từ Scan Report)

5. OPERATOR — "Khi chạy production..."
   Deploy, monitoring, backup, disaster recovery, scaling
   (Optional — cho projects cần production-readiness)
```

---

## 6. PROTOCOL GIAO TIẾP

### Chủ thầu → Thợ: Task Instruction Pack (TIP)

```
Mỗi TIP bao gồm:
• Header (ID, project, dependencies, priority)
• Context (working dir, key files, patterns to follow)
• Task (mô tả cụ thể)
• Specifications (business rules, validation, errors)
• Acceptance Criteria (Gherkin — testable)
• Constraints (boundaries, reuse requirements)
• Report Format (expected output)
```

### Thợ → Chủ thầu: Completion Report

```
Mỗi Report bao gồm:
• Status (DONE / PARTIAL / BLOCKED)
• Files Changed (created + modified)
• Test Results (AC pass/fail)
• Issues Discovered
• Deviations from Spec
• Suggestions
```

### Escalation Protocol

```
Level 1: Thợ tự giải quyết (implementation details)
Level 2: Thợ → Chủ thầu (spec ambiguity, pattern choice)
Level 3: Chủ thầu → Con người (scope, architecture, business rules)
```

---

## 7. NGUYÊN TẮC VÀNG v5.0

### 1. "Contractor-Worker Protocol"
```
Chủ thầu KHÔNG BAO GIỜ code.
Thợ KHÔNG BAO GIỜ thiết kế.
Con người KHÔNG BAO GIỜ phải dịch giữa hai bên.
```

### 2. "Đề xuất trước, hỏi sau"
```
Khi nhận yêu cầu → Scan → Đề xuất vision → RRI để customize
Không chờ lệnh. Không hỏi 100 câu trước khi bắt đầu.
```

### 3. "Executable, not just text"
```
TIP có acceptance criteria testable.
Report có status verifiable.
Verify có traceability measurable.
```

### 4. "Blueprint là khế ước"
```
Sau khi approved → Không thay đổi kiến trúc.
Thay đổi lớn → Quay lại Vision.
```

### 5. "Thợ không được phép sáng tạo"
```
Mọi sáng tạo xảy ra ở SCAN → RRI → VISION → BLUEPRINT.
Ở BUILD, Thợ tuân thủ TIP 100%.
Có ý tưởng hay? → Report lên, không tự làm.
```

### 6. "Verify mọi thứ"
```
Không ship mà không VERIFY.
VERIFY = RRI Reverse: mỗi requirement đã implement chưa?
Tier 1 phải 100% pass.
```

---

## 8. KẾT QUẢ DỰ KIẾN

### Effort Distribution

```
CON NGƯỜI (2-3 giờ tổng):
├── 30-45 phút: RRI interview
├── 15-20 phút: Review Blueprint
├── 10 phút: Approve Task Graph
├── 20-30 phút: Relay TIPs ↔ Reports
├── 15-20 phút: Review Verify Report
└── 15-20 phút: Refinement decisions

CHỦ THẦU (concurrent với Con người):
├── Context gathering
├── Smart question generation
├── Vision + Blueprint
├── TIP generation
├── Report analysis
├── RRI Reverse verification
└── Refinement TIPs

THỢ (execute):
├── Codebase scan
├── TIP implementation
├── Self-testing
├── Completion reporting
└── Fix implementation
```

### Metrics cải thiện

| Metric | v4.0 | v5.0 Target |
|--------|------|-------------|
| Requirements discovery | 4 giờ | 30-45 phút |
| Handoff quality | Copy-paste text | Executable TIPs |
| Feedback loop | Không có | Bidirectional |
| QA | Cosmetic refine | RRI Reverse |
| Rework | ~40% | <10% |
| Human effort | 6-8 giờ | 2-3 giờ |

---

## 9. TÓM TẮT

```
LIGHTKIT v5.0 = CONTEXT × PROTOCOL × VERIFICATION

CONTEXT:         Scan + RRI + Memory
PROTOCOL:        TIP + Completion Report + Escalation
VERIFICATION:    RRI Reverse + Requirement Traceability

= Production-ready software
  với < 10% rework
  trong 2-3 giờ human effort
```

---

*Lightkit v5.0 — "The Agentic Edition"*
*Chủ thầu điều phối, Thợ thi công, Con người ra quyết định.*
