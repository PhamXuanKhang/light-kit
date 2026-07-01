# Migration Guide: Lightkit v5 → v6

## What Changed

### Philosophy: Same Core, Broader Scope

v5 and v6 share the same core methodology (3 roles, 8 steps, RRI, TIP/Report protocol). The primary change in v6 is **generalization**: the framework no longer assumes web apps and works for any type of software project.

### Key Differences

| Aspect | v5 | v6 |
|--------|----|----|
| **Scope** | Web-focused (templates for Landing Page, SaaS, Dashboard, etc.) | General-purpose (any software type) |
| **Templates** | 5 project-specific templates (LANDING-PAGE, SAAS-APP, etc.) | No templates — Vision Guide derives architecture from first principles |
| **Question Bank** | Organized by project type | Organized by persona (End User, BA, QA, Dev, Operator) |
| **Scan Report** | JS/TS-specific (package.json, TypeScript strict, ESLint) | Language-agnostic (any manifest file, general code health) |
| **Vision** | Template matching → fill in blanks | 4-step process: Classify Dimensions → Derive Architecture → Design Direction → Tech Stack |
| **Design System** | Always included | Gated behind "if UI project" condition |
| **Packaging** | Multiple standalone files (PHILOSOPHY, Masters, etc.) | Single `.skill` file with references |
| **Enforcement** | None | Checkpoint Validation gates between every step |

### What Was Removed

| v5 Item | v6 Replacement |
|---------|---------------|
| `Templates/LANDING-PAGE.txt` | `vision-guide.md` (derive from dimensions) |
| `Templates/SAAS-APP.txt` | `vision-guide.md` (derive from dimensions) |
| `Templates/DASHBOARD.txt` | `vision-guide.md` (derive from dimensions) |
| `Templates/PORTFOLIO.txt` | `vision-guide.md` (derive from dimensions) |
| `Templates/BLOG-DOCS.txt` | `vision-guide.md` (derive from dimensions) |
| JS/TS-specific scan checks | General code health checks |
| Hardcoded "Next.js + Tailwind" references | Tech stack derived from requirements |

### What Was Added

| v6 Addition | Purpose |
|-------------|---------|
| `vision-guide.md` | Structured approach to proposing vision for any project type |
| 6 Project Dimensions | Interface, Data flow, User model, Lifecycle, Scale, State |
| Non-UI Design Considerations | CLI, API, Data Pipeline, Library/SDK patterns |
| Checkpoint Validation | Enforcement gates between every workflow step |
| `walkthrough-example.md` | End-to-end example of the 8-step workflow |
| `CASE-STUDIES.md` | Metrics collection framework and case study template |

---

## How to Migrate

### Step 1: Install the new skill

Replace your v5 skill/prompts with the v6 `.skill` file:
1. Open `lightkit.skill`
2. Click "Copy to your skills" in Claude
3. The v6 skill will replace v5 behavior

### Step 2: Update your mental model

The main shift: **stop thinking in templates, start thinking in dimensions.**

v5: "I'm building a SaaS app, so I use the SAAS-APP template."
v6: "My project has: Web UI + CRUD lifecycle + Multi-tenant user model + Team scale → derive architecture from these signals."

### Step 3: Adapt existing projects

If you have a project started with v5:

**RRI output is compatible** — REQ-IDs, Requirements Matrix, Decisions Log carry over unchanged.

**Blueprint may need updating** — v5 Blueprints often included template-specific sections. Review and ensure your Blueprint reflects the actual project structure, not a template.

**TIPs are fully compatible** — The TIP format and Completion Report format are identical between v5 and v6.

**Scan Report needs updating** — If your v5 Scan Report uses JS/TS-specific fields (e.g., "TypeScript Strict: Yes"), update to v6 format (e.g., "Type Safety: Strict"). See `tip-and-report-formats.md` for the canonical format.

### Step 4: Archive v5 files

Move these to your Archive folder (they are no longer used):
- `Templates/LANDING-PAGE-v4.txt` and all `-v4.txt` templates
- `PHILOSOPHY_V4.md` (superseded by V5, which is still valid)
- `*-v4.txt` master prompts (superseded by v5 masters)

Keep these (still valid):
- `PHILOSOPHY_V5.md` — Core philosophy hasn't changed, still relevant
- `Masters/*-v5.txt` — Debug, QA, X-Ray masters work independently
- `RRI-T_METHODOLOGY.docx`, `RRI-UX_METHODOLOGY.docx`, `RRI-UI_METHODOLOGY.docx` — Extended RRI methodologies

---

## FAQ

**Q: Do I need to redo RRI for existing projects?**
A: No. v5 RRI output is compatible with v6. The question bank reorganization (by persona instead of project type) only affects new interviews.

**Q: Can I still use the v5 Masters (DEBUG, QA, XRAY)?**
A: Yes. The v5 Masters in `Masters/` work independently and are compatible with v6.

**Q: What if I liked the template approach?**
A: The vision-guide.md approach is strictly more flexible — it can produce the same output as any template, plus handle project types templates couldn't. If you miss a specific template, use it as inspiration during the Vision step.

**Q: Is v6 backward compatible with v5?**
A: At the methodology level, yes. All v5 concepts (3 roles, 8 steps, TIP, RRI, Escalation) exist in v6. The workflow is identical. Only the reference files and organization have changed.
