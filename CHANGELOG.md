# Changelog — Lightkit

All notable changes to this project will be documented in this file.
Format follows [Keep a Changelog](https://keepachangelog.com/).

---

## [v7.0-draft] — 2026-06-28

### Added
- `skill-v7/SKILL.md` as a draft entry point for a compact, agent-agnostic product engineering workflow.
- `skill-v7/references/human-workflow.md` with the human-first workflow: Evidence Scan → Align → Explore → Decide → Detail → Execute.
- `skill-v7/references/agent-workflow.md` defining Solo Coding Agent, Agent + Reviewer, Multi-Agent, and Chat-Assisted modes.
- `skill-v7/references/compact-artifacts.md` with compact templates for Codebase Brief, Project Brief, PRD-lite, SSD Options, Decision Log, LLD, Task Graph, Execution Cards, and Verify Ledger.
- `skill-v7/references/verification-policy.md` with evidence-based verification rules and compact/full QA behavior.
- `skill-v7/references/migration-from-v6.md` mapping v6 concepts and artifacts to v7 equivalents.
- `skill-v7/references/source-map.md` to document the origin of internal concepts, external standards, and user-provided workflow sources.
- `skill-v7/sources/README.md` as a contributor-facing bibliography and source index.
- `skill-v7/sources/product-triangle-nexus-workflow.md` as the local Markdown source for the Nexus-style PRD → SSD → LLD workflow.
- v7 metrics in `CASE-STUDIES.md` for artifact count, report length, full report count, human relay count, decision-grade questions, auto-answered items, time to first code, context reloads, and verify evidence coverage.

### Changed
- `README.txt` now describes both v7 Draft and v6 Stable, with v7 as the recommended review/iteration track and v6 as the stable packaged skill.
- `CURRENT_VERSION.md` now distinguishes the v7 Draft track from the stable v6 package.
- `CASE-STUDIES.md` now includes separate templates for v7 Draft and v6 legacy/full workflow.

### Design Direction
- Shifted from a Claude Chat + Claude Code handoff model toward a coding-agent-first workflow with repo evidence.
- Replaced report-heavy defaults with compact output by default and expanded reports only on risk, failure, handoff, milestone, or explicit request.
- Reframed RRI as risk-based clarification instead of a fixed 40–60 question phase for every task.
- Introduced PRD-lite → SSD Options → Decision Log → LLD as the main planning chain.

---

## [v6.0] — 2026-03-17

### Changed
- **Framework is now general-purpose.** Removed all hardcoded project type examples (Landing Page, SaaS, Dashboard, Blog, Portfolio). The methodology now works for any software project type.
- `vision-patterns.md` replaced by `vision-guide.md` — teaches how to derive architecture from first principles using 6 project dimensions (Interface, Data flow, User model, Lifecycle, Scale, State) instead of matching against predefined templates.
- `rri-question-bank.md` reorganized from "by project type" to "by persona" — 5 universal personas with questions applicable to any project.
- `qa-protocol.md` test templates generalized — removed project-type-specific tests, kept tiered structure (Tier 1/2/3) with generic descriptions.
- `templates.md` removed project-type-specific file structures (Next.js SaaS/Landing/Dashboard).
- `tip-and-report-formats.md` generalized scan instruction for multi-language (package.json, pyproject.toml, Cargo.toml, go.mod).
- All pinned `Next.js 14` references removed — framework no longer prescribes specific framework versions.

### Added
- `CHANGELOG.md` (this file)
- `CURRENT_VERSION.md` with version info and roadmap
- `lightkit.skill` packaged installer file
- Workspace restructure: `Masters/` and `Archive/` directories

### Removed
- Project type detection table from SKILL.md Step 3
- Tech Stack Recommendations table (was hardcoded per project type)
- 6 project-specific layout diagrams from vision patterns
- File structure templates for specific frameworks

### Fixed
- Entry point (README.txt) now points to correct files and reflects v6
- Version consistency: all files now reference v6.0 (was fragmented across v3/v4/v5)

---

## [v5.0] — 2025-02

### Added
- Agentic Edition: Claude Chat (Chủ thầu) + Claude Code (Thợ thi công) separation
- TIP (Task Instruction Pack) format replacing old Coder Pack
- Completion Report format
- Escalation Protocol (3 levels)
- RRI 3.0: Context-aware adaptive interview with 3 question modes
- Debug Protocol (9 steps)
- QA Protocol (3 tiers)
- X-Ray Protocol (6 steps)
- RRI-T, RRI-UX, RRI-UI methodology extensions

### Changed
- Workflow expanded from templates to 8-step process
- Roles formalized into Power Triangle

---

## [v4.0] — 2024-12

### Added
- Detailed templates per project type (v4 variants)
- TRANSFORMATION_GUIDE.md
- LIGHTKIT_V4_AUDIT.md

### Changed
- Templates expanded with more detailed specifications

---

## [v3.0] — 2024-12

### Added
- Initial release
- 5 project type templates (Landing Page, SaaS, Dashboard, Blog, Portfolio)
- Basic README with 3-step usage guide
- ChatGPT-oriented workflow
