# Lightkit v7 — Human Workflow

Lightkit v7 bắt đầu từ quy trình làm việc của con người trước, sau đó mới chuyển hóa thành workflow cho AI agent. AI là chất xúc tác để scan, tạo nháp, phân tích trade-off, sinh task, implement và verify; AI không phải nguồn thay thế quyết định sản phẩm/kỹ thuật của con người.

## Core Workflow

```text
0. EVIDENCE SCAN
1. ALIGNMENT & SCOPING
2. EXPLORATION & OPTION GENERATION
3. DECISION & COMMITMENT
4. DETAILING & REFINEMENT
5. HIGH-PRECISION EXECUTION
```

Public shorthand:

```text
ALIGN → EXPLORE → DECIDE → DETAIL → EXECUTE
```

Evidence Scan là pre-step bắt buộc với existing codebase và tùy chọn với greenfield project.

---

## Phase 0 — Evidence Scan

### Mục tiêu

Hiểu hiện trạng trước khi hỏi hoặc thiết kế. Đây là phần kế thừa SCAN của Lightkit v6 nhưng rút gọn để tránh report dài.

### Khi dùng

- Existing codebase.
- Thêm feature vào repo có sẵn.
- Migration/refactor.
- Bugfix phức tạp.
- Trước khi ra quyết định kiến trúc dựa trên code hiện có.

### Output

`CODEBASE_BRIEF.md`

```markdown
# Codebase Brief

Stack:
Entry points:
Architecture:
Relevant files:
Existing tests:
Constraints:
Risks/gaps:
```

### Gate

- Stack/entry points đã xác định hoặc ghi rõ unknown.
- Relevant files/patterns đã có bằng chứng từ repo.
- Risks/gaps không bị biến thành quyết định nếu chưa có evidence.

---

## Phase 1 — Alignment & Scoping

### Mục tiêu

Thống nhất vấn đề, mục tiêu, phạm vi, non-goals và success criteria. Đây là nơi Product/Owner và Tech cùng tạo hiểu biết chung.

### Output

`PROJECT_BRIEF.md`

```markdown
# Project Brief

Problem:
Goal:
Users:
Scope:
Non-goals:
Constraints:
Success criteria:
Open decisions:
```

### Clarification policy

Dùng RRI theo hướng risk-based:

- Auto-answer từ Evidence Scan và tài liệu có sẵn.
- Chỉ hỏi khi câu trả lời ảnh hưởng đến scope, architecture, business rule, security, data, cost hoặc UX chính.
- Không bắt buộc 40–60 câu hỏi.
- Không bắt buộc đủ 5 personas cho task nhỏ.

### Gate

- Problem và goal rõ.
- Scope và non-goals có ranh giới.
- Success criteria testable.
- Open decisions được ghi lại, không bị giấu trong giả định.

---

## Phase 2 — Exploration & Option Generation

### Mục tiêu

Chuyển nhu cầu thành PRD-lite và tạo 2–3 phương án kỹ thuật cấp cao khi có nhiều cách hợp lý để làm.

### Outputs

- `PRD_LITE.md`
- `SSD_OPTIONS.md`

### PRD-lite template

```markdown
# PRD-lite

Context:
Users / actors:
User goals:
Functional requirements:
Non-functional requirements:
Out of scope:
Acceptance signals:
Open questions:
```

### SSD Options template

```markdown
# SSD Options

| Option | Summary | Impact | Effort | Risk | When to choose |
|---|---|---:|---:|---:|---|
| A | | | | | |
| B | | | | | |
| C | | | | | |

Recommendation:
Rationale:
```

### Khi chỉ cần một option

Nếu task nhỏ, pattern trong codebase đã rõ, hoặc constraint buộc một hướng duy nhất, không tạo 3 option giả. Ghi:

```markdown
Only one viable option because: [evidence]
```

### Gate

- PRD-lite bám vào Project Brief.
- SSD option có trade-off Impact/Effort/Risk.
- Recommendation không che giấu nhược điểm.

---

## Phase 3 — Decision & Commitment

### Mục tiêu

Con người chọn một hướng và commit vào trade-off. AI có thể khuyến nghị nhưng không tự quyết định các vấn đề sản phẩm, scope, architecture quan trọng hoặc chi phí/rủi ro cao.

### Output

`DECISION_LOG.md` hoặc `ADR-xxxx.md`

```markdown
# Decision: [Title]

Context:
Options considered:
Decision:
Why:
Trade-offs:
Consequences:
Review trigger:
```

### Gate

- Option được chọn rõ ràng.
- Lý do chọn được ghi lại.
- Trade-off và consequence không bị bỏ qua.
- Những quyết định cần owner approve đã được owner approve.

---

## Phase 4 — Detailing & Refinement

### Mục tiêu

Chuyển Selected SSD thành thiết kế đủ chi tiết để implement chính xác.

### Outputs

- `LLD.md`
- `TASK_GRAPH.md`
- `tasks/TASK-xxx.md`

### LLD template

```markdown
# Low-Level Design

Modules:
APIs / commands / UI entry points:
Data model:
State flow:
Business rules:
Error handling:
Test strategy:
Migration / compatibility:
```

### Task Graph template

```markdown
# Task Graph

| Task | Depends on | Goal | Verify |
|---|---|---|---|
| TASK-001 | None | | |
| TASK-002 | TASK-001 | | |
```

### Gate

- Mỗi task có goal và verify step.
- Task không trộn quá nhiều concern không liên quan.
- Dependency rõ.
- Không có P0 open decision trước execution.

---

## Phase 5 — High-Precision Execution

### Mục tiêu

Implement theo task, verify bằng evidence, báo cáo compact. Đây là nơi coding agent phát huy mạnh nhất vì có repo access và test execution.

### Outputs

- Changed files.
- Compact status report.
- `VERIFY_LEDGER.md`.

### Compact report

```markdown
DONE TASK-001
Changed:
- path/file.ts — change summary
Verified:
- npm test PASS
Issues:
- None
```

### Full report chỉ dùng khi

- BLOCKED hoặc PARTIAL.
- Test/build/lint fail.
- Deviation khỏi spec.
- Phát hiện security/data/migration risk.
- Handoff cho người/agent khác.
- User yêu cầu.

### Gate

- Acceptance criteria được verify hoặc ghi rõ vì sao chưa verify được.
- Không ship nếu P0 fail.
- Deviation/risk phải được surfaced, không giấu trong report compact.

---

## Mapping từ Lightkit v6 sang v7

| v6 Step | v7 Human Workflow | Action |
|---|---|---|
| SCAN | Evidence Scan | Giữ, compact thành Codebase Brief. |
| RRI | Alignment / PRD-lite clarification | Giữ lõi, risk-based, không fixed question count. |
| VISION | Exploration | Thay bằng PRD-lite + SSD Options. |
| BLUEPRINT | Selected SSD + LLD | Tách high-level decision và low-level design. |
| CONTRACT | Decision Record | Thay bằng ADR/Decision Log khi không cần contract dài. |
| TASK GRAPH | LLD → Execution Cards | Giữ, nhưng task card ngắn hơn TIP. |
| BUILD | Execute | Giữ. |
| VERIFY | Verify Ledger | Giữ traceability, compact by default. |
| REFINE | Refine | Giữ, phân loại fix/polish/scope change. |

## Tier sử dụng

V7 dùng right-sized mandatory workflow: luôn route task trước, nhưng chỉ tạo artifact đủ để giữ chất lượng quyết định.

| Tier | Khi dùng | Artifact tối thiểu | Verify | Review |
|---|---|---|---|---|
| Tiny | Typo, text, config nhỏ, câu hỏi code | Không artifact; trích file path/evidence khi trả lời | Quick Verify nếu có thay đổi | Không |
| Small | Bugfix, simple refactor, small feature theo pattern rõ | Direct evidence hoặc Task Card ngắn | Quick/Task Verify | Không, trừ khi risk override |
| Medium | Behavior mới, vài file, endpoint/command/UI flow | Project Brief ngắn, PRD-lite hoặc one-option rationale, Task Graph, Verify Ledger | Task Verify | Optional theo risk |
| Large | Module/product lớn, architecture, migration rộng | Full PRD-lite, SSD Options, Decision Log/ADR, LLD, Task Graph, Verify Ledger/QA | Milestone QA | Có nếu risk cao |
| High-risk override | Auth, security, privacy, data/schema migration, billing, public API, outward-facing release | Decision record + LLD/task cards đủ rollback/verify | Deep Verify | Bắt buộc, trừ khi human defer |
| Handoff/Audit | Bàn giao/onboarding/audit | Handoff pack + current decisions + verify status + risks | Review/QA evidence | Theo mục tiêu |

### TDD trong execution

Nếu behavior testable, ưu tiên `RED → GREEN → REFACTOR`:

1. Thêm hoặc xác định test đang fail.
2. Xác nhận fail đúng lý do.
3. Implement thay đổi nhỏ nhất.
4. Xác nhận pass.
5. Refactor chỉ khi cần và không đổi behavior.

Nếu test-first không thực tế, ghi rõ lý do và dùng evidence khác: build/typecheck, static inspection, manual scenario, runtime check hoặc review.
