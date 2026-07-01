---
name: lightkit-v7-draft
description: >
  Lightkit v7 Draft — Compact, agent-agnostic product engineering workflow.
  Use when the user wants a low-token coding-agent workflow, human-first product/tech process,
  Spec-Driven Development, PRD-lite → SSD → LLD planning, evidence-based execution, senior AI engineer operating mode, compact reports, teaching/understanding sessions, or migration from Lightkit v6.
---

# Lightkit v7 Draft — Compact Agent-Agnostic Product Engineering Workflow

## Core Philosophy

```text
Human workflow first. Agent execution second.
Repo evidence beats chat assumptions.
Compact by default. Expand only on risk or failure.
Spec guides implementation. Evidence updates specs.
```

V7 keeps the useful discipline of Lightkit v6 — Evidence Scan, RRI, acceptance criteria, Debug, QA, Verify — but changes the operating model:

- No default dependency on Claude Chat + Claude Code.
- No long reports by default.
- No fixed 40–60 RRI question target for every task.
- No manual paste relay as the main workflow.
- One coding agent with repo access is the default execution surface.

## Core Workflow

```text
0. EVIDENCE SCAN
1. ALIGNMENT & SCOPING
2. EXPLORATION & OPTION GENERATION
3. DECISION & COMMITMENT
4. DETAILING & REFINEMENT
5. HIGH-PRECISION EXECUTION
```

Short form:

```text
ALIGN → EXPLORE → DECIDE → DETAIL → EXECUTE
```

Evidence Scan is a pre-step for existing codebases.
## Senior AI Engineer Mode

V7 can operate as a senior AI engineer operating model: one agent may investigate, align, specify, plan, implement, verify, review risk, teach, and hand off.

Senior autonomy has boundaries:

- autonomous on local implementation details that match existing patterns;
- collaborative on product, architecture, data, security, billing, cost, public API, and release-risk decisions;
- evidence-bound on all codebase claims.

Read: `references/senior-ai-engineer.md`.

## Spec-Driven Compatibility

V7 is compatible with Spec Kit-style Spec-Driven Development without requiring full ceremony for every task.

Mapping:

```text
Specify -> PRD-lite / Spec
Plan    -> SSD Options / LLD / Decisions
Tasks   -> Task Graph / Task Cards
Build   -> High-Precision Execution
Analyze -> Convergence Check
```

Use full SDD for Medium/Large/high-risk work. Use SDD Lite for Tiny/Small work.

Read: `references/spec-driven-development.md` and `references/command-protocols.md`.

## Task Size & Risk Router

V7 is a right-sized mandatory workflow: always route the task before acting, but use the smallest process that preserves decision quality.

| Route | Use when | Minimum workflow | Do not create by default |
|---|---|---|---|
| Tiny | Typo, wording, simple config, direct repo question | Inspect evidence → answer/patch → quick verify if applicable | `.lightkit/`, PRD-lite, SSD, LLD |
| Small | Bugfix, simple refactor, small feature in known pattern | Evidence → short plan/task card → implement → verify evidence | Full PRD/SSD/LLD unless risk escalates |
| Medium | Behavior change across a few files, new endpoint/command/UI flow | Project Brief → PRD-lite or one-option rationale → Task Graph → Verify Ledger | Fake 3-option SSD |
| Large | New module/product, architecture decision, broad migration | Full PRD-lite → SSD Options → Decision Log/ADR → LLD → Task Graph → Verify Ledger/QA | Compact-only execution |
| Audit/Handoff | Onboarding, review, release, transfer to another person/agent | Handoff pack with file paths, decisions, risks, verify status | Long pasted context |

### Risk override

Escalate one level, and usually require human decision/review, when the task touches auth, security, privacy, data/schema migration, billing/payment, public API, dependencies with operational impact, irreversible/destructive action, or outward-facing release behavior.

Hard rules:

- Use the smallest artifact set that preserves decision quality.
- Do not create three fake options when only one viable option exists.
- Do not ask the user for facts that can be read from the repo.
- Do not report `DONE` unless verification evidence exists; use `PARTIAL`, `BLOCKED`, or `UNVERIFIED` instead.

## Responsibilities, Not Platforms

| Responsibility | Owner | Notes |
|---|---|---|
| Human decision owner | User / product owner | Decides scope, business rules, trade-offs, risk acceptance. |
| Product-tech planner | Human + AI agent | Creates PRD-lite, SSD options, decision records, LLD. |
| Executor / verifier | Coding agent | Implements, tests, verifies with evidence. |
| Reviewer | Optional second agent/human | Used for architecture, security, QA, migration, release risk. |

The old language of Chủ nhà / Chủ thầu / Thợ can still be used as metaphor, but v7 does not bind those roles to Claude Chat, Claude Code, Codex, Cursor, or any other specific tool.

## Operating Modes

### Mode 1 — Solo Coding Agent (default)

Use one coding agent with repo access for scan, planning, implementation and verification.

### Mode 2 — Agent + Reviewer

Use when changes are security-sensitive, architecture-heavy, release-critical, or need independent QA.

### Mode 3 — Multi-Agent Orchestration

Use only for large audits, broad migrations, or multi-perspective verification. Do not use multi-agent orchestration just because the old workflow had multiple roles.

### Mode 4 — Chat-Assisted

Use chat for brainstorming or decision support only. Chat-only planning must not be the source of truth for existing codebase decisions without an Evidence Scan.

Read: `references/agent-workflow.md`.

## Artifact Policy

Default artifact set for Medium+ work:

```text
.lightkit/
  codebase-brief.md
  project-brief.md
  prd-lite.md
  ssd-options.md
  decisions.md
  lld.md
  task-graph.md
  tasks/
    TASK-001.md
  verify-ledger.md
  teaching-checklist.md
```

If the project should not create `.lightkit/`, keep the same artifact structure in a temporary or docs folder. Tiny/Small work may use inline notes instead of files.

Read: `references/compact-artifacts.md` and `references/artifact-lifecycle.md`.

## Compact Output Rule

Routine success:

```markdown
DONE TASK-001
Changed: 3 files
Verified: npm test PASS
Issues: None
```

Expand only when:

- task is `BLOCKED` or `PARTIAL`;
- build/test/lint/typecheck fails;
- implementation deviates from spec;
- there is security, privacy, data, migration, or outward-facing risk;
- handoff to another human/agent is required;
- the user explicitly asks for full detail.

## RRI in v7

RRI remains a clarification technique, not a mandatory long interview.

Use:

```text
“I see it like this — correct?”
```

Ask only decision-grade questions:

- product scope;
- business rule;
- architecture;
- data model/migration;
- security/privacy;
- cost/provider;
- irreversible or outward-facing action;
- important UX direction.

Do not ask the user things that can be answered by reading the repo.

## Phase Gates

### Evidence Gate

- Codebase facts are backed by file paths, commands, or direct inspection.
- Unknowns are marked as unknown, not guessed.

### Alignment Gate

- Problem, goal, scope, non-goals, and success criteria are clear.
- Open decisions are recorded.

### Decision Gate

- Selected SSD or one-option rationale is recorded.
- Trade-offs are explicit.
- Human approval exists for scope/architecture/risk decisions.

### Execution Gate

- Task graph exists for multi-step work.
- Each task has goal, files, acceptance, and verify step.
- No unresolved P0 decision remains.

### Verify Gate

- Pass has evidence.
- Untested does not count as pass.
- P0 failures block release unless explicitly deferred by human.

Read: `references/verification-policy.md`.

## Special Protocols

V7 keeps v6 protocols but changes output verbosity:

- Debug: evidence → hypotheses → root cause → fix → verify.
- QA: tiered verification, compact by default, full report for milestone/release.
- X-Ray: use for handoff/onboarding/audit, not routine small tasks.
- Teaching Session: use when the user wants incremental teaching, restatement, quizzes, and a running mastery checklist.
- Convergence: use when spec, plan, tasks, code, tests, or docs may have drifted.

## When to Use Full Workflow

Use full workflow for Large or high-risk work:

- new product/module;
- large feature;
- significant architecture decision;
- data model or migration;
- auth/security/privacy/billing behavior;
- public API or outward-facing release behavior;
- multi-stakeholder requirements;
- handoff/release.

Use v7 Lite for Tiny/Small work:

- bugfix;
- small feature;
- simple refactor;
- narrow QA/debug task.

Lite still requires evidence and verification. It only removes unnecessary artifacts.

## TDD and Review Rules

- If behavior is testable, prefer `RED → GREEN → REFACTOR`: add or identify a failing test, confirm it fails for the expected reason, implement the smallest fix, confirm pass, then refactor only if useful.
- If test-first is not practical, record why and use the next best evidence: build/typecheck, static inspection, manual scenario, runtime check, or independent review.
- High-risk work requires review evidence before `DONE`, unless the human explicitly accepts the risk and defers review.

## Reference Files

| File | Purpose |
|---|---|
| `sources/README.md` | Source index for local documents, external links, and internal v6 references. |
| `references/source-map.md` | Maps concepts to internal/external origins and citations. |
| `references/human-workflow.md` | Human-first workflow based on Evidence Scan + Nexus-style phases. |
| `references/compact-artifacts.md` | Templates and compact/full output policy. |
| `references/agent-workflow.md` | Agent-agnostic operating model. |
| `references/verification-policy.md` | Evidence-based verification and gates. |
| `references/migration-from-v6.md` | How to migrate from v6 artifacts and roles to v7. |
| `references/teaching-session.md` | Protocol for teaching sessions with incremental mastery checks and running checklist. |

## Golden Rules

1. Start from evidence, not assumptions.
2. Use the smallest artifact that preserves decision quality.
3. Ask fewer but better questions.
4. Keep context in files, not paste chains.
5. Make trade-offs explicit before committing.
6. Implement in small verifiable tasks.
7. Report compactly unless risk/failure requires detail.
8. Do not bind the workflow to a specific agent platform.
9. Specs guide implementation; evidence updates specs.
10. Senior autonomy stops at product and risk boundaries.
11. Check convergence before handoff, release, or long-running `DONE` claims.
