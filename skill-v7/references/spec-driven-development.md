# Lightkit v7 - Spec-Driven Development Bridge

Use this reference when a task needs Spec Kit-style discipline: a clear spec, implementation plan, task list, and consistency checks before or during build.

## Principle

```text
Specification guides implementation. Evidence updates specification.
```

V7 uses Spec-Driven Development as a right-sized workflow, not as mandatory ceremony for every edit.

## Spec Kit concept mapping

| Spec Kit concept | V7 equivalent | Purpose |
|---|---|---|
| Specify | Project Brief / PRD-lite | Define problem, users, scope, functional needs, acceptance signals. |
| Plan | SSD Options / LLD | Decide technical approach, constraints, modules, data flow, test strategy. |
| Tasks | Task Graph / Task Cards | Break the plan into small verifiable implementation units. |
| Implement | High-Precision Execution | Apply code/docs changes task by task. |
| Analyze | Convergence Check | Detect contradictions across spec, plan, tasks, code, tests. |
| Clarify | RRI | Ask only decision-grade questions. |
| Checklist | Verify Ledger / QA checklist | Track acceptance, regression, release, and teaching checks. |
| Constitution | Project principles / constraints | Record non-negotiable technical and product rules. |
| Converge | Drift recovery | Re-align code, tasks, specs, and remaining work. |

## When to use full SDD

Use full SDD for:

- new product or module;
- multi-file feature or workflow;
- public API or outward-facing behavior;
- architecture decision;
- data/schema migration;
- auth, security, privacy, billing, or compliance risk;
- release or handoff where traceability matters.

Minimum artifact chain:

```text
Evidence -> Spec -> Plan -> Tasks -> Implement -> Verify -> Converge
```

## When to use SDD Lite

Use SDD Lite for Tiny/Small work:

- typo, wording, direct config edit;
- narrow bugfix with obvious local pattern;
- simple refactor with no behavior change;
- direct codebase question.

Lite still requires evidence and verification, but may use a short task note instead of full spec/plan/tasks.

## Artifact rules

- A spec states desired behavior, not implementation trivia.
- A plan explains technical approach and trade-offs.
- A task has one goal, expected files or area, acceptance, and verify step.
- Implementation that deviates from spec must update spec, plan, tasks, or decision log.
- Verification must connect back to acceptance signals.

## Senior judgment

Do not create fake options when constraints imply one viable path. Record:

```markdown
Only one viable option because: [evidence]
```

Do not ask the user to decide facts that can be read from the repo. Ask only when the answer changes scope, business rules, architecture, data, security, cost, UX direction, or irreversible behavior.

## Convergence trigger

Run a convergence check when:

- implementation took multiple turns;
- tasks changed during execution;
- tests revealed hidden behavior;
- the user asks whether work is complete;
- handoff/release is near;
- docs/spec may no longer match code.
