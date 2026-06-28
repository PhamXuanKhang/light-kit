# Vibecode Kit v7 — Verification Policy

Verification trong v7 phải dựa trên evidence, không dựa trên cam kết bằng lời. Tuy nhiên, report phải compact mặc định để tránh token overhead.

## Core rules

1. Pass requires evidence.
2. Untested is not pass.
3. Failures must include the exact evidence needed to reproduce or understand them.
4. P0 failures block ship unless human explicitly defers with rationale.
5. Full QA report is milestone/risk behavior, not routine behavior.

---

## Verification levels

| Level | Khi dùng | Output |
|---|---|---|
| Quick Verify | Task nhỏ, bugfix | Compact status + command result summary |
| Task Verify | Mỗi execution card | Update Verify Ledger |
| Milestone QA | Sau nhóm task / trước release | QA summary hoặc full QA report |
| Deep Verify | Security/data/migration/high-risk | Full evidence, reviewer optional |

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
