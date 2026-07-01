# Lightkit v7 — Compact Artifacts

Mục tiêu của v7 là giảm token/context overhead bằng cách dùng artifact ngắn, có cấu trúc, chỉ mở rộng khi có rủi ro hoặc thất bại.

## Output policy

```text
Compact by default.
Expand only on risk, failure, handoff, milestone, or explicit user request.
```

### Dùng compact khi

- Task nhỏ hoặc trung bình.
- Không có architecture change.
- Test/build pass.
- Không có deviation.
- Không cần handoff cho người/agent khác.

### Dùng full artifact/report khi

- BLOCKED/PARTIAL.
- Test/build/lint fail.
- Có deviation khỏi spec.
- Có security/data/migration/outward-facing risk.
- Cần quyết định của owner.
- Milestone/release/QA sign-off.
- User yêu cầu rõ.

---

## 1. `CODEBASE_BRIEF.md`

Dùng thay Scan Report dài.

```markdown
# Codebase Brief

Stack:
- Language:
- Framework:
- Data/storage:
- Test/build tools:

Entry points:
- 

Architecture / patterns:
- 

Relevant files:
- `path` — why relevant

Existing tests:
- Command:
- Coverage / known gaps:

Constraints:
- 

Risks/gaps:
- 
```

Target length: 50–100 dòng.

---

## 2. `PROJECT_BRIEF.md`

Dùng cho Alignment & Scoping.

```markdown
# Project Brief

Problem:

Goal:

Users / actors:

Scope:
- In:
- Out:

Constraints:

Success criteria:

Open decisions:
```

Target length: 1 trang.

---

## 3. `PRD_LITE.md`

Dùng để mô tả “cái gì” ở mức đủ cho kỹ thuật.

```markdown
# PRD-lite

Context:

Users / actors:

User goals:

Functional requirements:
- REQ-001:
- REQ-002:

Non-functional requirements:
- Performance:
- Security:
- Accessibility:
- Operations:

Out of scope:

Acceptance signals:

Open questions:
```

Target length: 1–3 trang tùy scope.

---

## 4. `SSD_OPTIONS.md`

Dùng để so sánh phương án kỹ thuật cấp cao.

```markdown
# SSD Options

Context:

| Option | Summary | Impact | Effort | Risk | When to choose |
|---|---|---:|---:|---:|---|
| A | | Low/Med/High | Low/Med/High | Low/Med/High | |
| B | | Low/Med/High | Low/Med/High | Low/Med/High | |
| C | | Low/Med/High | Low/Med/High | Low/Med/High | |

Recommendation:

Rationale:

Known trade-offs:
```

Nếu chỉ có một phương án hợp lý:

```markdown
Only one viable option:
Reason:
Evidence:
Risks:
```

---

## 5. `DECISION_LOG.md` hoặc `ADR-xxxx.md`

Dùng thay Contract dài khi mục tiêu là ghi quyết định kỹ thuật/sản phẩm.

```markdown
# Decision Log

## D-001: [Title]

Context:
Options considered:
Decision:
Why:
Trade-offs:
Consequences:
Review trigger:
```

Quy tắc:

- Ghi quyết định ảnh hưởng scope, architecture, data, security, cost, UX chính.
- Không ghi các chi tiết implementation nhỏ nếu không cần traceability.

---

## 6. `LLD.md`

Dùng để mô tả “làm như thế nào” đủ để implement.

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

Target: vừa đủ để tạo task. Không viết tutorial hoặc giải thích lan man.

---

## 7. `TASK_GRAPH.md`

```markdown
# Task Graph

Route:
- Size: Tiny / Small / Medium / Large
- Risk: Low / Medium / High / Critical
- Review required: Yes / No

| Task | Depends on | Goal | Verify | Risk |
|---|---|---|---|---|
| TASK-001 | None | | | Low/Med/High |
| TASK-002 | TASK-001 | | | Low/Med/High |

Critical path:

Parallelizable tasks:

Deferred tasks:
```

---

## 8. `tasks/TASK-xxx.md`

Dùng thay TIP mặc định.

```markdown
# TASK-001: [Name]

Size: Tiny / Small / Medium / Large
Risk: Low / Medium / High / Critical
Review required: Yes / No
Verify level: Quick / Task / Milestone / Deep

Goal:

Files:
- `path` — expected change

Steps:
1. 
2. 
3. 

Test / TDD plan:
- RED:
- GREEN:
- REFACTOR:
- If no test-first: reason + alternate evidence

Acceptance:
- [ ] 
- [ ] 

Do not:
- 

Verify:
- Command:
- Expected:
```

### Khi cần full TIP

Chỉ mở rộng task card thành full TIP khi:

- Giao task cho agent/người khác không có context.
- Business logic phức tạp.
- Task chạm data migration/security/payment/auth.
- Nhiều dependency hoặc rollback requirement.

---

## 9. `VERIFY_LEDGER.md`

Dùng thay Verify Report dài mặc định.

```markdown
# Verify Ledger

| Item | Requirement / Task | Evidence | Status | Notes |
|---|---|---|---|---|
| 1 | TASK-001 / REQ-001 | `npm test` PASS | PASS | |
| 2 | TASK-001 / TDD-RED | Test failed before fix for expected reason | PASS | Optional when TDD applies |
| 3 | TASK-002 / REQ-002 | Manual check | PASS | |

Open issues:

Decisions needed:

Review evidence:
- Required: Yes / No
- Verdict:

Overall status: READY / NEEDS FIXES / BLOCKED
```

### Status values

- `PASS` — có evidence.
- `FAIL` — có evidence fail.
- `PARTIAL` — hoạt động một phần, ghi rõ gap.
- `SKIP` — không áp dụng hoặc deferred có lý do.
- `UNVERIFIED` — chưa có evidence, không được xem là pass.

---

## Compact status formats

### Done

```markdown
DONE TASK-001
Changed: 3 files
Verified: npm test PASS
Issues: None
```

### Partial

```markdown
PARTIAL TASK-001
Done:
Blocked:
Evidence:
Decision needed:
```

### Blocked

```markdown
BLOCKED TASK-001
Blocker:
Evidence:
Tried:
Options:
Recommendation:
```

### Failed verification

```markdown
VERIFY FAIL
Failed item:
Evidence:
Likely cause:
Next action:
```

## Token budget rules

- Prefer tables and bullet lists over prose.
- Do not paste unchanged long context back to the user.
- Reference file paths instead of duplicating content.
- Summarize pass results; expand only fail/block/risk.
- Keep routine reports under 15 lines.
