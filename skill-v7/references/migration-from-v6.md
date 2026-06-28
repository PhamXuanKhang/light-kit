# Migration from Vibecode Kit v6 to v7 Draft

V7 không xóa giá trị của v6. V7 giữ các phần mạnh của v6 nhưng đổi cách vận hành để giảm token, giảm copy-paste và bỏ phụ thuộc Claude Chat / Claude Code như nền tảng mặc định.

## Summary

| v6 | v7 Draft |
|---|---|
| 8-step workflow | 5-phase human workflow + Evidence Scan |
| Claude Chat / Claude Code mapping | Agent-agnostic responsibilities |
| RRI 40–60 questions target | Risk-based clarification |
| Vision / Blueprint / Contract | PRD-lite / SSD Options / Decision Record / LLD |
| TIP | Execution Card compact |
| Completion Report | Compact report by default |
| Verify Report | Verify Ledger by default |
| Manual paste handoff | Workspace artifact files |

---

## What stays

- Evidence-first SCAN.
- RRI philosophy: “I see it like this — correct?”
- Requirement traceability.
- Acceptance criteria.
- Debug protocol principles.
- QA/Verify before ship.
- Human owns strategic decisions.

## What changes

### 1. Role model

V6:

```text
Chủ thầu = Claude Chat
Thợ thi công = Claude Code
```

V7:

```text
Product-tech design responsibility
Execution / verification responsibility
Human decision responsibility
```

Các responsibility này có thể do một coding agent đảm nhiệm theo mode khác nhau, hoặc tách ra khi cần review độc lập.

### 2. Workflow

V6:

```text
SCAN → RRI → VISION → BLUEPRINT → TASK GRAPH → BUILD → VERIFY → REFINE
```

V7:

```text
EVIDENCE SCAN → ALIGN → EXPLORE → DECIDE → DETAIL → EXECUTE
```

### 3. Artifacts

| v6 artifact | v7 replacement | Notes |
|---|---|---|
| Scan Report | Codebase Brief | Ngắn hơn, evidence-focused. |
| RRI Report | Project Brief + PRD-lite | RRI trở thành clarification technique, không phải report dài mặc định. |
| Vision | PRD-lite + SSD Options | Tách product intent và technical options. |
| Blueprint | Selected SSD + LLD | Tách high-level architecture và low-level design. |
| Contract | Decision Log / ADR | Ghi quyết định và trade-off thay vì contract dài. |
| TIP | Task Card / Execution Card | Full TIP chỉ khi handoff hoặc risk cao. |
| Completion Report | Compact status | Full report chỉ khi partial/blocked/fail/deviation. |
| Verify Report | Verify Ledger | Full QA report khi milestone/release. |

---

## Migration steps

### Step 1 — Keep v6 intact

Không sửa `skill-v6` khi thử v7. Tạo `skill-v7` như draft độc lập.

### Step 2 — Convert role language

Trong tài liệu mới, thay platform mapping bằng responsibility mapping:

```markdown
Human decision owner
Product-tech planner
Executor / verifier
```

Có thể vẫn dùng từ Chủ nhà / Chủ thầu / Thợ để giải thích, nhưng không gắn cứng vào Claude Chat / Claude Code.

### Step 3 — Convert workflow references

Khi thấy v6 step, đổi theo bảng:

```markdown
SCAN -> Evidence Scan
RRI -> Alignment clarification / PRD-lite discovery
VISION -> Exploration / SSD options
BLUEPRINT -> Selected SSD / LLD
CONTRACT -> Decision Record
TASK GRAPH -> Task Graph + Execution Cards
BUILD -> Execute
VERIFY -> Verify Ledger / QA
REFINE -> Refine gate
```

### Step 4 — Convert report formats

Routine success report:

```markdown
DONE TASK-001
Changed: 3 files
Verified: npm test PASS
Issues: None
```

Only expand when needed:

```markdown
BLOCKED / PARTIAL / VERIFY FAIL / DEVIATION
```

### Step 5 — Convert handoff

V6 handoff:

```text
Paste TIP into Claude Code
Paste Completion Report back
```

V7 handoff:

```text
Write/read workspace artifacts
Point next agent/person to file paths
```

Example:

```markdown
Read:
- `.vibecode/project-brief.md`
- `.vibecode/lld.md`
- `.vibecode/tasks/TASK-003.md`
```

---

## Usage tiers

### v7 Lite

Use for bugfix/small feature.

Required:

- Codebase Brief or direct evidence.
- Task Card.
- Verify evidence.

### v7 Standard

Use for normal feature.

Required:

- Project Brief.
- PRD-lite.
- Selected SSD or one-option rationale.
- Task Graph.
- Verify Ledger.

### v7 Full

Use for product/module-level work.

Required:

- Full Evidence Scan.
- PRD-lite.
- SSD Options.
- Decision Log/ADR.
- LLD.
- Task Graph.
- Verify Ledger / QA Report.

### v7 Audit/Handoff

Use for onboarding, handover, review.

Required:

- X-Ray or equivalent codebase documentation.
- Current decisions.
- Verify status.
- Open risks.

---

## Breaking changes to expect

- Existing prompts that assume Claude Chat as Contractor should be rewritten.
- Existing templates requiring long Completion Reports should become compact by default.
- RRI gates based on fixed question count should become risk/coverage gates.
- Contract approval language should move to Decision Log/ADR approval where appropriate.
- TIP handoff should move from paste blocks to workspace artifact references.

## Compatibility

V6 remains useful for:

- teaching the original methodology;
- full formal workflow;
- protocol references like Debug, QA, X-Ray;
- historical case comparison.

V7 should become the default for day-to-day coding-agent work after at least one case study confirms lower overhead.
