# Changelog — Vibecode Kit

All notable changes to this project will be documented in this file.
Format follows [Keep a Changelog](https://keepachangelog.com/).

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
- `vibecode-kit.skill` packaged installer file
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
- VIBECODE_KIT_V4_AUDIT.md

### Changed
- Templates expanded with more detailed specifications

---

## [v3.0] — 2024-12

### Added
- Initial release
- 5 project type templates (Landing Page, SaaS, Dashboard, Blog, Portfolio)
- Basic README with 3-step usage guide
- ChatGPT-oriented workflow
