# Lightkit v7 — Verification Policy

Verification trong v7 phải dựa trên evidence, không dựa trên cam kết bằng lời. Tuy nhiên, report phải compact mặc định để tránh token overhead.

## Core rules

1. Pass requires evidence.
2. Untested is not pass.
3. Failures must include the exact evidence needed to reproduce or understand them.
4. P0 failures block ship unless human explicitly defers with rationale.
5. Full QA report is milestone/risk behavior, not routine behavior.
6. `DONE` is invalid without verification evidence; use `PARTIAL`, `BLOCKED`, or `UNVERIFIED` instead.

---

## Verification before completion

Before reporting `DONE`, the agent must answer:

| Question | Required answer |
|---|---|
| What was checked? | Requirement, task, or acceptance criterion. |
| How was it checked? | Command, manual steps, static inspection, runtime check, or reviewer verdict. |
| What happened? | PASS/FAIL/PARTIAL/SKIP/UNVERIFIED with evidence. |
| What remains? | Open issue, defer rationale, or None. |

`UNVERIFIED` never counts as `PASS`. `SKIP` is allowed only when the check is not applicable or explicitly deferred with a reason.

---

## Verification levels

| Level | Khi dùng | Output |
|---|---|---|
| Quick Verify | Tiny/Small, bugfix | Compact status + command result summary |
| Task Verify | Small/Medium execution card | Update Verify Ledger |
| Milestone QA | Sau nhóm task / trước release | QA summary hoặc full QA report |
| Deep Verify | Security/data/migration/high-risk | Full evidence + reviewer verdict |

## Size/Risk verification matrix

| Route | Required evidence | Review |
|---|---|---|
| Tiny + Low | Static inspection or quick command when a file changes | No |
| Small + Low | Relevant test/build/typecheck/manual check, or reason unavailable | No |
| Medium | Task Verify in Verify Ledger | Optional by risk |
| Large | Milestone QA + Verify Ledger | Recommended |
| High/Critical risk | Deep Verify + human decision/defer rationale | Required |

Risk overrides size: high-risk work cannot be marked `DONE` with only a quick visual or static check.

---

## Evidence types

| Evidence | Ví dụ |
|---|---|
| Automated test | `npm test`, `pytest`, `cargo test`, `go test ./...` |
| Build/typecheck | `npm run build`, `tsc --noEmit`, `mypy`, `cargo check` |
| Manual scenario | Steps + observed result |
| Static inspection | File path + line reference |
| Runtime check | Local server response, API call, screenshot if UI |
| Review | Independent reviewer finding/verdict |

## Verify Ledger template

```markdown
# Verify Ledger

| Item | Requirement / Task | Evidence | Status | Notes |
|---|---|---|---|---|
| 1 | TASK-001 / REQ-001 | `npm test` PASS | PASS | |

Open issues:

Decisions needed:

Overall status: READY / NEEDS FIXES / BLOCKED
```

## Status definitions

- `PASS`: evidence confirms expected behavior.
- `FAIL`: evidence shows expected behavior is not met.
- `PARTIAL`: some acceptance criteria pass, some do not.
- `SKIP`: intentionally not applicable or explicitly deferred.
- `UNVERIFIED`: not checked; cannot count as pass.

---

## TDD / regression policy

Use the lightest test discipline that fits the codebase:

| Situation | Preferred action |
|---|---|
| Bugfix with existing test harness | Add or identify a failing regression test before the fix. |
| New behavior | Write a test or acceptance check before implementation when practical. |
| Simple refactor | Run existing tests/typecheck to prove behavior did not change. |
| Legacy/no-test area | Record why test-first is not practical and use build/static/manual/runtime evidence. |
| High-risk change | Combine automated evidence with review evidence. |

TDD shorthand:

```text
RED → GREEN → REFACTOR
```

- `RED`: failing test observed for the expected reason.
- `GREEN`: smallest implementation makes the test pass.
- `REFACTOR`: cleanup only after passing evidence; do not expand scope.

---

## Acceptance criteria style

Use the lightest testable form.

### Checklist form

Good for simple tasks:

```markdown
Acceptance:
- [ ] Button appears only for signed-in users.
- [ ] Click opens confirmation dialog.
- [ ] Cancel leaves data unchanged.
```

### Gherkin form

Use when behavior has meaningful state/action/result:

```gherkin
Given a signed-in admin
When they click Delete Project
Then a confirmation dialog is shown
```

Gherkin should stay concise. Do not create verbose scenarios just to satisfy format.

---

## Release gate

Before ship/release:

- P0 requirements: 100% PASS or explicitly deferred by human.
- Critical issues: 0 open.
- Build/typecheck/test command: PASS or documented reason unavailable.
- Security/data migration risks: reviewed.
- Required reviewer verdict: PASS or explicitly deferred by human.
- Verify Ledger overall status: READY.

## Refine gate

Refinement can proceed without returning to decision phase only if changes are:

- copy/text changes;
- small UI polish within approved layout;
- bugfixes that preserve behavior intent;
- test additions;
- minor implementation cleanup caused by current task.

Return to Decision/Detail if change requires:

- new feature;
- architecture change;
- schema/data migration;
- auth/security behavior change;
- new provider/dependency with operational impact;
- changed success criteria.
