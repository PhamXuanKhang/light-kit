# Lightkit — Case Studies & Metrics Framework

## Purpose

This document provides templates for documenting real projects built with Lightkit, along with metrics for evaluating methodology effectiveness. Each case study should show not only whether the project shipped, but also how much planning, reporting, human relay, and rework the workflow created.

---

## Metrics Collection Framework

### Core Metrics — v6 / full workflow

Use these when evaluating the original v6-style workflow or any full formal process.

| Metric | How to Measure | Target (v6) |
|--------|---------------|-------------|
| **RRI Duration** | Time from first RRI question to RRI Report complete | 30-45 minutes |
| **Total Human Effort** | Sum of all time Human spends (RRI + review + relay + decisions) | 2-3 hours |
| **Requirements Count** | Number of REQ-IDs in Requirements Matrix | 15-50 |
| **RRI Question Count** | Total questions asked across all personas | 40-60 |
| **Persona Coverage** | Number of personas consulted out of 5 | 5/5 (or 4/5 with justification) |
| **TIP Count** | Number of TIPs generated | Varies by project |
| **First-Pass TIP Success** | TIPs completed DONE on first attempt / total TIPs | >80% |
| **Rework Rate** | TIPs requiring re-implementation / total TIPs | <10% |
| **Requirement Coverage** | REQ-IDs implemented / total REQ-IDs (from Verify Report) | >95% P0, >85% overall |
| **Scenario Pass Rate** | Scenarios passed / total scenarios (from Verify Report) | >90% |
| **Escalation Count** | Level 2 + Level 3 escalations during BUILD | Track, no target |
| **Scope Drift Incidents** | Times Builder added features not in TIP (caught in review) | 0 |

### Compact Workflow Metrics — v7 draft

Use these to verify whether v7 actually reduces token/context overhead and manual relay.

| Metric | How to Measure | Target (v7 draft) |
|--------|---------------|-------------------|
| **Artifact Count** | Number of methodology artifacts created for the project | Lite: 1-3, Standard: 4-7, Full: as needed |
| **Average Report Length** | Average routine status report length in lines | Routine success: <=15 lines |
| **Full Report Count** | Number of expanded reports triggered by risk/failure/handoff | Track, should be exception not default |
| **Human Relay Count** | Number of manual copy-paste handoffs between tools/agents | Solo mode: 0-1 |
| **Decision-Grade Questions Asked** | Questions requiring human judgment on scope/risk/trade-off | Track; lower is better if decisions remain sound |
| **Auto-Answered Items** | Questions answered from repo/docs without asking human | Track; higher indicates better evidence use |
| **Time to First Code** | Time from request to first implementation edit | Track vs v6/project baseline |
| **Context Reload / Recap Count** | Times the workflow required re-summarizing lost context | Track; target near 0 with workspace artifacts |
| **Verify Evidence Coverage** | Tasks with concrete evidence / total tasks | 100% for completed tasks |
| **First-Pass Task Success** | Tasks completed and verified on first attempt / total tasks | >80% |
| **Rework Rate** | Tasks requiring re-implementation / total tasks | <10% |

### Quality Metrics (collect when possible)

| Metric | How to Measure |
|--------|---------------|
| **Build Success** | Project builds without errors after all tasks complete |
| **Type Safety** | Type errors remaining at Verify (0 = good) |
| **Test Coverage** | Automated test coverage % (if applicable) |
| **Critical Bugs at Verify** | Bugs found during VERIFY phase |
| **Post-Ship Issues** | Issues found after shipping (within 7 days) |
| **Security Findings** | Security issues found during review/QA |
| **Data/Migration Issues** | Data loss, schema drift, rollback, migration defects |

### Comparison Metrics (if available)

| Metric | Without Lightkit | v6 Workflow | v7 Draft Workflow |
|--------|---------------------|-------------|-------------------|
| Time to first working version | [hours] | [hours] | [hours] |
| Time to first code | [hours] | [hours] | [hours] |
| Rework cycles | [count] | [count] | [count] |
| Missing requirements discovered late | [count] | [count] | [count] |
| Human decisions required | [count] | [count] | [count] |
| Manual relay count | [count] | [count] | [count] |
| Average routine report length | [lines] | [lines] | [lines] |
| Artifact count | [count] | [count] | [count] |

---

## Case Study Template — v7 Draft

Copy the template below for projects using the compact workflow.

```markdown
# Case Study: [Project Name]

## Project Overview
- **Type:** [Web app / API / CLI / Mobile / Data pipeline / Other]
- **Description:** [1-2 sentences]
- **Tech Stack:** [Languages, frameworks, databases]
- **Workflow Tier:** [Lite / Standard / Full / Audit-Handoff]
- **Operating Mode:** [Solo Coding Agent / Agent + Reviewer / Multi-Agent / Chat-Assisted]
- **Date:** [When built]
- **Starting Point:** [New project / Existing codebase with X files]

## Workflow Summary

### Evidence Scan
- Codebase Brief created: [Yes/No]
- Key findings: [Brief summary]
- Auto-answered items: [X]

### Alignment
- Project Brief created: [Yes/No]
- Decision-grade questions asked: [X]
- Open decisions after alignment: [X]

### Explore → Decide
- PRD-lite created: [Yes/No]
- SSD options generated: [0/1/2/3]
- Decision records created: [X]
- Chosen approach: [Summary]

### Detail → Execute
- LLD created: [Yes/No]
- Task cards generated: [X]
- Tasks completed first pass: [X/Y]
- Tasks requiring rework: [X]
- Full reports triggered: [X]

### Verify
- Verify Ledger created: [Yes/No]
- Verify evidence coverage: [X/Y]
- Build/typecheck/test status: [PASS/FAIL/SKIP]
- Critical issues found: [X]
- Deferred items: [X]

## Metrics Summary

| Metric | Value |
|--------|-------|
| Total Human Effort | [X hours] |
| Time to First Code | [X minutes/hours] |
| Artifact Count | [X] |
| Average Routine Report Length | [X lines] |
| Full Report Count | [X] |
| Human Relay Count | [X] |
| Decision-Grade Questions Asked | [X] |
| Auto-Answered Items | [X] |
| Task Count | [X] |
| First-Pass Task Success | [X]% |
| Rework Rate | [X]% |
| Verify Evidence Coverage | [X]% |

## Lessons Learned
- [What worked well]
- [What could be improved]
- [Unexpected challenges]
- [Where compact reporting was insufficient, if any]

## Comparison (if applicable)
- Previous attempt without methodology: [describe outcome]
- v6-style workflow estimate/result: [describe overhead]
- v7 draft workflow result: [describe improvement]
```

---

## Case Study Template — v6 / Legacy Full Workflow

Copy the template below for projects using the original v6 methodology.

```markdown
# Case Study: [Project Name]

## Project Overview
- **Type:** [Web app / API / CLI / Mobile / Data pipeline / Other]
- **Description:** [1-2 sentences]
- **Tech Stack:** [Languages, frameworks, databases]
- **Team:** [Who played which role — Homeowner, Contractor tool, Builder tool]
- **Date:** [When built]
- **Starting Point:** [New project / Existing codebase with X files]

## Lightkit Flow

### SCAN
- Scan type: [Light / Full / Focused]
- Key findings: [Brief summary]

### RRI
- Duration: [X minutes]
- Questions asked: [X total, across Y personas]
- Personas consulted: [list]
- REQ-IDs generated: [X]
- Key decisions made: [X]

### VISION → BLUEPRINT
- Architecture type: [e.g., Monolith, Microservice, Serverless]
- Blueprint review time: [X minutes]
- Revisions before approval: [X]

### TASK GRAPH → BUILD
- TIPs generated: [X]
- TIPs completed DONE first pass: [X/Y]
- TIPs requiring rework: [X]
- Escalations: Level 2: [X], Level 3: [X]
- Scope drift incidents: [X]

### VERIFY
- Requirement coverage: [X]%
- Scenarios passed: [X/Y]
- Critical issues found: [X]
- Minor issues found: [X]

### REFINE
- Refinement cycles: [X]
- Issues fixed: [X]

## Metrics Summary

| Metric | Value |
|--------|-------|
| Total Human Effort | [X hours] |
| RRI Duration | [X minutes] |
| Requirements Count | [X REQ-IDs] |
| TIP Count | [X] |
| First-Pass Success | [X]% |
| Rework Rate | [X]% |
| Requirement Coverage | [X]% |
| Scenario Pass Rate | [X]% |

## Lessons Learned
- [What worked well]
- [What could be improved]
- [Unexpected challenges]

## Comparison (if applicable)
- Previous attempt without methodology: [describe outcome]
- With Lightkit: [describe improvement]
```

---

## Recorded Case Studies

> Add case studies below as projects are completed.

### [No case studies recorded yet]

To add a case study:
1. Pick the v7 or v6 template.
2. Fill in metrics as you go through the workflow.
3. Complete the Lessons Learned section after shipping or stopping.
4. Add the completed case study under Recorded Case Studies.
