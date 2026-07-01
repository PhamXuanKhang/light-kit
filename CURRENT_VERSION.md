# Lightkit — Current Version

## Recommended Track: v7 Draft

**Draft date:** 2026-06-28  
**Codename:** Compact Agent-Agnostic Workflow  
**Status:** Draft / under review  
**Location:** `skill-v7/`

Lightkit v7 is the new draft direction for the project. It keeps the strongest parts of v6 — Evidence Scan, RRI, acceptance criteria, Debug, QA, Verify — but reframes the methodology as a human-first product engineering workflow that can be executed by any capable coding agent.

Core v7 workflow:

```text
EVIDENCE SCAN → ALIGN → EXPLORE → DECIDE → DETAIL → EXECUTE
```

Key goals:

1. Reduce long report/token overhead.
2. Remove default dependency on Claude Chat + Claude Code split.
3. Prefer one coding agent with repo access for day-to-day work.
4. Move from `VISION → BLUEPRINT → CONTRACT` to `PRD-lite → SSD Options → Decision Log → LLD`.
5. Use compact artifacts and expand only on risk, failure, handoff, milestone, or explicit user request.
6. Track sources clearly for future GitHub contributors.

## Stable Track: v6.0

**Release date:** 2026-03-17  
**Codename:** General-Purpose Edition  
**Status:** Stable  
**Location:** `skill-v6/` and `lightkit.skill`

Lightkit v6 is the current stable installable methodology. It uses 3 roles (Chủ nhà / Chủ thầu / Thợ thi công) and an 8-step workflow to turn ideas into working software.

v6 workflow:

```text
SCAN → RRI → VISION → BLUEPRINT → TASK GRAPH → BUILD → VERIFY → REFINE
```

Key difference from v5: the framework no longer assumes you're building a specific type of web app. It works for web apps, mobile apps, CLIs, APIs, data pipelines, or anything else.

## Canonical Files

| File | Purpose | Status |
|------|---------|--------|
| `skill-v7/SKILL.md` | v7 draft entry point | **Recommended for review/iteration** |
| `skill-v7/references/` | v7 workflow references | Draft supporting docs |
| `skill-v7/sources/` | v7 source bibliography and local references | Contributor source tracking |
| `lightkit.skill` | Installable skill package | **Stable v6 package** |
| `skill-v6/SKILL.md` | v6 main skill instructions | Stable source of truth |
| `skill-v6/references/` | v6 reference files | Stable supporting docs |
| `PHILOSOPHY_V5.md` | Core methodology philosophy | Reference |
| `Masters/*-v5.txt` | Standalone protocol prompts | Usable independently |
| `CASE-STUDIES.md` | Metrics framework + v6/v7 templates | Active |
| `MIGRATION.md` | v5 → v6 migration guide | Reference |

## What's New in v7 Draft

1. **Human-first workflow** — starts from product/tech workflow before converting to agent workflow.
2. **Agent-agnostic responsibilities** — Human decision owner, Product-tech planner, Executor/verifier, optional Reviewer.
3. **Nexus-inspired PRD → SSD → LLD chain** — adds SSD as the bridge between product requirements and implementation design.
4. **Compact artifacts** — Codebase Brief, Project Brief, PRD-lite, SSD Options, Decision Log, LLD, Task Graph, Execution Card, Verify Ledger.
5. **Compact report policy** — routine success reports stay short; full reports only on risk/failure/handoff/milestone/request.
6. **Risk-based RRI** — RRI remains “I see it like this — correct?” but no fixed 40–60 question target for every task.
7. **Workspace artifact context** — prefer files under `.lightkit/` or equivalent over manual copy-paste relay.
8. **Source tracking** — `skill-v7/sources/README.md` and `skill-v7/references/source-map.md` document origins and citations.
9. **Overhead metrics** — `CASE-STUDIES.md` now tracks artifact count, report length, human relay count, time to first code, context reloads, and verify evidence coverage.

## What's Included in v6.0

1. **Enforcement layer** — `SKILL.md` includes Checkpoint Validation gates between every workflow step. Each gate has specific checkboxes that must pass before proceeding.
2. **Design System Defaults gated** — `vision-guide.md` gates font pairing, color psychology, and content patterns behind an explicit "UI Projects Only" condition.
3. **Case studies framework** — `CASE-STUDIES.md` provides metrics collection framework and reusable case study templates.
4. **Migration guide** — `MIGRATION.md` documents differences between v5 and v6 with step-by-step migration instructions.
5. **General-purpose throughout** — scan, debug, QA and RRI references are generalized for multiple project types and languages.

## Remaining Known Gaps

1. **v7 is draft, not packaged** — `lightkit.skill` still points to the stable v6 package.
2. **No runtime tooling** — both v6 and v7 are docs-first methodologies, not executable CLI tools.
3. **No recorded v7 case studies yet** — metrics and templates exist, but real-world validation is still needed.
4. **Some best-practice concepts need deeper citation** — ADR, QA standards, security checklists, and DevOps practices should be mapped to stronger sources before being treated as formal standards.

## Roadmap

### v7 draft validation (next)

- Run 1-3 small case studies using v7 Lite / Standard.
- Measure report length, artifact count, human relay count, and time to first code.
- Decide whether v7 should replace v6 as the packaged `lightkit.skill`.
- Add missing citations for ADR/security/DevOps practices if they become core.

### v7 packaging (future)

- Package v7 into `lightkit.skill` after review.
- Keep v6 archived as stable legacy methodology.
- Add smoke test script for link/reference integrity.
- Consider runtime tooling only after workflow validation.

### Runtime tooling (future)

- `vibe init`
- `vibe brief`
- `vibe task`
- `vibe verify`
- Optional multi-agent orchestration for large audits/migrations only.
