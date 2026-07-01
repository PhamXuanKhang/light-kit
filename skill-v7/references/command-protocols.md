# Lightkit v7 - Command Protocols

Use these command-like protocols to route user intent quickly. They are conceptual commands; they do not require a CLI.

## Protocol index

| Protocol | Use when | Primary output |
|---|---|---|
| `/v7.scan` | Need repo or context evidence | Codebase Brief / evidence notes |
| `/v7.align` | Need problem, scope, success criteria | Project Brief |
| `/v7.spec` | Need desired behavior captured | PRD-lite / Spec |
| `/v7.plan` | Need technical approach | SSD Options / LLD / Decision Log |
| `/v7.tasks` | Need execution breakdown | Task Graph / Task Cards |
| `/v7.build` | Need implementation | Changed files + verification |
| `/v7.verify` | Need proof of correctness | Verify Ledger / QA result |
| `/v7.review` | Need independent or risk review | Review verdict |
| `/v7.teach` | Need human mastery | Teaching Checklist |
| `/v7.converge` | Need drift detection | Convergence report |
| `/v7.handoff` | Need transfer of context | Handoff Pack |

## `/v7.scan`

Goal: establish facts before planning or coding.

Minimum output:

```markdown
Evidence:
- path/file: relevant fact
Unknowns:
- ...
Risks:
- ...
```

Gate: major claims have file, command, log, or direct inspection evidence.

## `/v7.align`

Goal: clarify problem, goal, scope, non-goals, constraints, and success criteria.

Ask only decision-grade questions. If the repo answers it, inspect instead of asking.

Gate: success criteria are testable or explicitly marked as qualitative.

## `/v7.spec`

Goal: capture desired behavior before design or implementation.

Use for Medium+ work or any outward-facing behavior.

Minimum sections:

```markdown
Context:
Users / actors:
Functional requirements:
Non-functional requirements:
Out of scope:
Acceptance signals:
Open questions:
```

Gate: no hidden P0 scope or business-rule decision remains.

## `/v7.plan`

Goal: choose a technical approach and expose trade-offs.

Use one-option rationale when only one path is viable. Use SSD Options when there are real alternatives.

Gate: selected approach, consequences, and verification strategy are clear.

## `/v7.tasks`

Goal: convert plan into small verifiable work.

Each task needs:

```markdown
Goal:
Files / area:
Acceptance:
Verify:
Depends on:
```

Gate: each task can be completed and verified independently enough to reduce risk.

## `/v7.build`

Goal: implement the smallest safe task.

Rules:

- Touch only files required by the task.
- Match existing style.
- Update artifacts when behavior or decisions change.
- Do not mark done before verification evidence exists.

## `/v7.verify`

Goal: prove acceptance or state the verification gap.

Evidence may include tests, typecheck, lint, build, runtime check, manual scenario, static inspection, or independent review.

Do not convert unavailable verification into pass.

## `/v7.review`

Goal: get independent risk or quality review.

Reviewer input:

```markdown
Goal:
Changed files / diff:
Verify evidence:
Risk areas:
Decision records:
```

Reviewer output:

```markdown
REVIEW VERDICT: PASS / NEEDS FIXES / BLOCKED
Findings:
- Severity:
  Evidence:
  Impact:
  Fix required:
```

## `/v7.teach`

Goal: help the human deeply understand the session.

Read `references/teaching-session.md`. Use the teaching checklist, restatement loop, quizzes, and mastery gate.

## `/v7.converge`

Goal: detect and repair drift across spec, plan, tasks, code, tests, and docs.

Check:

- implementation matches spec;
- completed tasks have verification evidence;
- code did not add unapproved behavior;
- tests cover acceptance signals where practical;
- docs/handoff reflect public behavior changes;
- remaining tasks and risks are explicit.

Output:

```markdown
CONVERGENCE: PASS / DRIFT FOUND / BLOCKED
Matches:
Drift:
Risks:
Next actions:
```

## `/v7.handoff`

Goal: transfer context without long paste chains.

Output:

```markdown
# Handoff Pack

Goal:
Read first:
Current status:
Changed files:
Verify evidence:
Risks:
Decisions:
Next task:
```
