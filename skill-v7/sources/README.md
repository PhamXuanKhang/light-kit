# Sources for Vibecode Kit v7

This folder contains local/source materials used to design Vibecode Kit v7 Draft. Keep these files in the repository so future contributors can trace where concepts came from.

## Local sources

| File | Purpose | Notes |
|---|---|---|
| `product-triangle-nexus-workflow.md` | Repository Markdown copy of “Tam giác sản phẩm - Quy trình làm việc mới” | Source for Nexus-style human workflow, PRD → SSD → LLD, and AI usage guidance. |
| `product-triangle-nexus-workflow.pdf` | Original local PDF: “Tam giác sản phẩm - Quy trình làm việc mới” | Optional binary source. Include when repository policy allows PDFs. |
| `product-triangle-nexus-workflow.pdf.md` | Raw Markdown conversion of the same PDF | Optional raw extraction artifact. Include when available. |

## External sources

| Source | URL | Used for |
|---|---|---|
| Agile Manifesto | https://agilemanifesto.org/ | Guardrail against document-heavy workflow: working software and collaboration over excessive handoff. |
| Cucumber Gherkin Reference | https://cucumber.io/docs/gherkin/reference/ | Given/When/Then acceptance criteria and executable specifications. |
| W3C WCAG 2.2 | https://www.w3.org/TR/WCAG22/ | Accessibility criteria for UI/accessibility checks. |
| Keep a Changelog | https://keepachangelog.com/en/1.1.0/ | Changelog convention for release documentation. |

## Internal Vibecode sources

| Source | Used for |
|---|---|
| `../../skill-v6/SKILL.md` | v6 roles, 8-step workflow, gates, protocols. |
| `../../skill-v6/references/rri-methodology.md` | RRI, RRI-T, RRI-UX, RRI-UI methodology family. |
| `../../skill-v6/references/tip-and-report-formats.md` | Scan Report, RRI Report, Blueprint, TIP, Completion Report, Verify Report formats. |
| `../../skill-v6/references/debug-protocol.md` | Evidence-first debugging process. |
| `../../skill-v6/references/qa-protocol.md` | Tiered QA and verification principles. |
| `../../CURRENT_VERSION.md` | Current v6 status, known gaps, roadmap. |
| `../../CASE-STUDIES.md` | Metrics framework and case study templates. |

## Contributor rule

When adding a new concept to v7, also update `../references/source-map.md` with:

1. concept name;
2. origin;
3. source link or local file path;
4. whether the concept is kept, adjusted, or removed.
