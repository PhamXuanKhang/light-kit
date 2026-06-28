# Vibecode Kit v7 — Agent Workflow

V7 chuyển human workflow thành operating model cho coding agent. Agent workflow phải agent-agnostic: dùng được với Claude Code, Codex CLI, Cursor, Aider, Amp hoặc bất kỳ coding agent nào có khả năng đọc/sửa file và chạy kiểm tra.

## Principle

```text
Human workflow first. Agent execution second.
Repo evidence beats chat assumptions.
```

Chat-only agent có thể hỗ trợ brainstorm hoặc decision support, nhưng không phải source of truth cho codebase vì không đọc/chạy repo trực tiếp.

---

## Operating Modes

### Mode 1 — Solo Coding Agent (default)

Một coding agent đảm nhiệm scan, plan, implement và verify trong cùng workspace.

Dùng khi:

- Task nhỏ/trung bình.
- Existing codebase cần đọc trực tiếp.
- Không cần independent review.
- Muốn giảm copy-paste và context relay.

Flow:

```text
User ↔ Coding Agent
          ├─ Evidence Scan
          ├─ Alignment / clarify
          ├─ PRD-lite / SSD / LLD as needed
          ├─ Execute task cards
          └─ Verify ledger
```

### Mode 2 — Agent + Reviewer

Một agent implement, một agent review.

Dùng khi:

- Security-sensitive change.
- Architecture decision quan trọng.
- Refactor lớn.
- Release/milestone QA.
- Cần adversarial review.

Reviewer không cần nhận report dài. Reviewer cần:

- goal;
- changed files/diff;
- verify evidence;
- risk areas.

### Mode 3 — Multi-Agent Orchestration

Chỉ dùng khi scale thật sự cần: audit lớn, migration nhiều module, research rộng, independent verification nhiều chiều.

Không dùng multi-agent chỉ vì workflow cũ có Chủ thầu/Thợ.

### Mode 4 — Chat-Assisted

Chat dùng cho:

- brainstorming;
- wording;
- option discussion;
- decision support.

Không dùng chat-only để kết luận pattern codebase nếu chưa có Evidence Scan từ coding agent.

---

## Workspace memory

Thay vì copy-paste TIP/Report qua chat, agent đọc/ghi artifact trong workspace:

```text
.vibecode/
  codebase-brief.md
  project-brief.md
  prd-lite.md
  ssd-options.md
  decisions.md
  lld.md
  task-graph.md
  tasks/
    TASK-001.md
    TASK-002.md
  verify-ledger.md
```

Nếu project không muốn tạo thư mục `.vibecode/`, các artifact có thể nằm trong docs/workspace tạm. Nhưng nguyên tắc vẫn là: context nằm trong file, không nằm trong chuỗi copy-paste chat.

---

## Agent execution loop

```text
1. Read current artifact/context.
2. Scan evidence if needed.
3. Identify missing decisions.
4. Ask only decision-grade questions.
5. Create/update compact artifact.
6. Execute smallest safe task.
7. Verify with evidence.
8. Report compactly.
9. Expand only on failure/risk/blocker.
```

## Decision-grade questions

Agent chỉ nên hỏi user khi câu trả lời ảnh hưởng một trong các mục sau:

- product scope;
- business rule;
- architecture;
- data model/migration;
- security/privacy;
- cost/provider;
- irreversible/outward-facing action;
- UX direction quan trọng.

Không hỏi user về chi tiết agent có thể kiểm chứng từ repo.

---

## Role translation

| v6 language | v7 responsibility | Notes |
|---|---|---|
| Chủ nhà / Homeowner | Human decision owner | Giữ quyền quyết định scope/trade-off. |
| Chủ thầu / Contractor | Product-tech designer / planner | Có thể là cùng coding agent ở planning mode. |
| Thợ thi công / Builder | Executor / verifier | Có thể là cùng coding agent ở execution mode. |

V7 giữ separation of concerns nhưng không gắn cứng mỗi responsibility với một nền tảng.

---

## Builder creativity policy

Thay rule “Builder không sáng tạo” bằng rule thực tế hơn:

- Agent không được tự ý đổi product scope hoặc architecture đã duyệt.
- Agent được phép chọn implementation detail nhỏ phù hợp pattern hiện có.
- Nếu spec mâu thuẫn codebase, agent phải surface evidence và đề xuất hướng xử lý.
- Nếu cần đổi dependency, schema, public API, security behavior hoặc migration, phải xin quyết định trước.

---

## Compact reporting for agents

Default:

```markdown
DONE TASK-001
Changed: 3 files
Verified: npm test PASS
Issues: None
```

When blocked:

```markdown
BLOCKED TASK-001
Blocker:
Evidence:
Options:
Recommendation:
```

When deviation:

```markdown
DEVIATION TASK-001
Spec said:
Codebase evidence:
Change made / proposed:
Impact:
Decision needed:
```

---

## Handoff rule

Nếu phải handoff cho agent/người khác, tạo handoff pack bằng file path, không paste toàn bộ context nếu không cần:

```markdown
# Handoff Pack

Goal:
Read first:
- `.vibecode/project-brief.md`
- `.vibecode/lld.md`
- `.vibecode/tasks/TASK-003.md`
Current status:
Verify evidence:
Risks:
Decision needed:
```

---

## Anti-patterns

- Chat-only planning over existing repo without Evidence Scan.
- Long reports for successful routine tasks.
- Creating 3 fake architecture options when only one viable option exists.
- Asking user questions that can be answered by reading code.
- Manual copy-paste relay as the default workflow.
- Multi-agent orchestration without a scale/review reason.
