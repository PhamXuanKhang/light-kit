# Vibecode Kit — Current Version

## Version: 6.0

**Release date:** 2026-03-17
**Codename:** General-Purpose Edition
**Status:** Stable

## What's in v6

Vibecode Kit v6 is a general-purpose AI-assisted software development methodology. It uses 3 roles (Chủ nhà / Chủ thầu / Thợ thi công) and an 8-step workflow to turn ideas into working software.

Key difference from v5: the framework no longer assumes you're building a specific type of web app. It works for web apps, mobile apps, CLIs, APIs, data pipelines, or anything else.

## Canonical Files

| File | Purpose | Status |
|------|---------|--------|
| `vibecode-kit.skill` | Installable skill package | **Primary entry point** |
| `skill-v6/SKILL.md` | Main skill instructions | Source of truth |
| `skill-v6/references/` | 9 reference files | Supporting docs |
| `PHILOSOPHY_V5.md` | Core methodology philosophy | Reference (still valid) |
| `Masters/*-v5.txt` | Standalone protocol prompts | Usable independently |
| `CASE-STUDIES.md` | Metrics framework + case study template | **New** |
| `MIGRATION.md` | v5 → v6 migration guide | **New** |

## What's Deprecated

| File/Folder | Reason | Location |
|-------------|--------|----------|
| Templates/ (v3/v4) | Replaced by general-purpose vision-guide | `Archive/Templates/` |
| README.txt v3 | Pointed to wrong files, wrong version | Replaced |
| `[TÀI-LIỆU-THAM-KHẢO]` | Old reference docs with broken links | `Archive/` |
| `*-v4.txt` masters | Superseded by v5 | `Archive/` |
| `PHILOSOPHY_V4.md` | Superseded by v5 | `Archive/` |

## What's Included in v6.0

1. **Enforcement layer** — `SKILL.md` includes Checkpoint Validation gates between every workflow step. Each gate has specific checkboxes that must pass before proceeding (e.g., RRI→VISION gate verifies all 5 personas consulted, minimum 30 questions asked, P0 questions answered).
2. **Design System Defaults gated** — `vision-guide.md` gates font pairing, color psychology, and content patterns behind an explicit "UI Projects Only" condition. Non-UI project considerations (CLI, API, Data Pipeline, Library/SDK) included.
3. **Case studies framework** — `CASE-STUDIES.md` provides metrics collection framework (core + quality + comparison metrics) and a reusable case study template.
4. **Migration guide** — `MIGRATION.md` documents all differences between v5 and v6 with step-by-step migration instructions.
5. **General-purpose throughout** — `scan-report-format.md` references canonical format in `tip-and-report-formats.md` (single source of truth). `debug-protocol.md` bug patterns and investigation commands cover Python, Go, Rust alongside JS/TS. `rri-question-bank.md` QA questions generalized for all project types.

## Remaining Known Gaps

1. **No runtime tooling** — v6 is a docs-first methodology, not an executable tool. CLI commands (`vibe new`, `vibe verify`) remain aspirational.
2. **No recorded case studies yet** — The metrics framework exists but no projects have been formally documented using it.

## Roadmap

### v6.1 (next)
- Record first 3-5 case studies using the new metrics framework
- Smoke test script for link/reference integrity
- Add industry-specific question bank extensions (healthcare, fintech, e-commerce)

### v7.0 (future)
- Runtime tooling: `vibe new`, `vibe pack-architect`, `vibe pack-coder`, `vibe verify`
- Automated QA integration (generate test scripts from acceptance criteria)
- Multi-agent orchestration (auto-relay TIP/Report without human bridge)
- Skill marketplace for community-contributed question banks
