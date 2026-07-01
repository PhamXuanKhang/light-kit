# Lightkit v7 - Artifact Lifecycle

Use this reference when work spans more than a single obvious edit, or when traceability matters across idea, spec, code, verification, review, teaching, and handoff.

## Lifecycle

```text
Request
-> Evidence
-> Problem / Scope
-> Spec
-> Plan
-> Tasks
-> Code
-> Verification
-> Review
-> Teaching / Handoff
-> Convergence
```

## Artifact chain

| Stage | Artifact | Required for |
|---|---|---|
| Evidence | `codebase-brief.md` or notes | Existing repo decisions, bug diagnosis, audits |
| Problem / Scope | `project-brief.md` | Medium+ work, ambiguous goals |
| Spec | `prd-lite.md` or `spec.md` | Desired behavior, acceptance, non-goals |
| Plan | `ssd-options.md`, `lld.md`, `decisions.md` | Architecture, trade-offs, implementation approach |
| Tasks | `task-graph.md`, `tasks/TASK-xxx.md` | Multi-step execution |
| Code | changed files | Implementation |
| Verification | `verify-ledger.md` | Done claims, release confidence |
| Review | review notes/verdict | High-risk or release-critical work |
| Teaching | `teaching-checklist.md` | Human understanding goal |
| Handoff | handoff pack | Transfer to human or another agent |
| Convergence | convergence report | Drift detection and recovery |

## Traceability rules

- Every major implementation task traces to a spec, plan, task card, or explicit user request.
- Every completed task has verification evidence or an explicit verification gap.
- Every deviation updates the relevant spec, plan, decision, task, or risk note.
- Every Critical/High risk is fixed, reviewed, or explicitly deferred by the human decision owner.
- Every teaching checkpoint records what the human demonstrated, not just what the agent explained.

## Artifact minimization

Tiny work may skip files and use compact evidence in the final response.

Small work may use a short inline task note.

Medium+ work should create or update workspace artifacts unless the repo policy says not to. If `.lightkit/` is not appropriate, use an agreed docs or temporary workspace path.

## Drift repair

When drift is found:

1. State the mismatch.
2. Identify source of truth: user decision, current code, spec, tests, or production constraint.
3. Update the stale artifact or code.
4. Re-run appropriate verification.
5. Record remaining risk.

## Done standard

A task is done only when:

- scope is satisfied or deferred explicitly;
- changed files are intentional;
- verification evidence exists or gap is stated;
- spec/task/code drift is acceptable or repaired;
- unresolved risks are visible.
