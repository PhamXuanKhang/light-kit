# Lightkit v7 - Teaching Session Protocol

Use this protocol when the user asks the agent to teach during a coding/debugging/planning session, verify their understanding incrementally, keep a running checklist, quiz them, or avoid ending until they demonstrate mastery.

## Core intent

Turn the session into a guided apprenticeship without stopping delivery work. Teach the human the problem, solution, and impact as the work unfolds.

```text
Do the work. Explain the why. Verify understanding before moving on.
```

## Activation

When this protocol is active:

- State the current teaching stage before major work.
- Ask the human to restate their understanding before filling gaps.
- Teach high-level motivation and low-level mechanics together.
- Keep a running Markdown checklist in the workspace.
- Quiz with varied open-ended and multiple-choice questions.
- Do not reveal quiz answers until after the human responds.
- Continue until the human demonstrates understanding or explicitly changes the goal.

If the environment provides an `AskUserQuestion`-style tool, use it for quizzes. If not, ask directly in chat and wait.

## Running checklist artifact

Create or update a Markdown file such as:

```text
.lightkit/teaching-checklist.md
```

If `.lightkit/` is not appropriate for the repo, place it in the active docs/workspace location and state the path.

Template:

```markdown
# Teaching Checklist

Goal:
Current stage:

## 1. Problem Understanding
- [ ] Can state the user-visible problem.
- [ ] Can explain why the problem existed.
- [ ] Can identify relevant branches, paths, states, or flows.
- [ ] Can name the evidence used to diagnose it.

## 2. Solution Understanding
- [ ] Can state what changed.
- [ ] Can explain why this solution was chosen.
- [ ] Can describe design decisions and trade-offs.
- [ ] Can reason through edge cases.
- [ ] Can connect tests/verification to the intended behavior.

## 3. Broader Context
- [ ] Can explain why the change matters.
- [ ] Can identify what users, systems, files, or workflows are impacted.
- [ ] Can name risks, limitations, or follow-up checks.

## Demonstrations
- Prompt:
- Human restatement:
- Gaps filled:
- Quiz result:
- Mastery status:
```

Update this file after each teaching stage, not only at the end.
## Hooks into v7 senior workflow

Teaching can overlay any v7 protocol:

| Workflow stage | Human should be able to explain |
|---|---|
| `/v7.scan` | What evidence was found, what remains unknown, and why evidence matters. |
| `/v7.align` | The problem, goal, scope, non-goals, and success criteria. |
| `/v7.spec` | Desired behavior, acceptance signals, and boundaries. |
| `/v7.plan` | The chosen design, rejected alternatives, trade-offs, and risks. |
| `/v7.tasks` | How tasks decompose the work and why dependencies exist. |
| `/v7.build` | What changed in code and how the main path and edge cases flow. |
| `/v7.verify` | Why the evidence proves or does not prove correctness. |
| `/v7.converge` | Whether spec, plan, tasks, code, tests, and docs still match. |
| `/v7.handoff` | What another human or agent must know to continue safely. |

For Spec-Driven Development work, add checklist items for spec, plan, tasks, and convergence only when those artifacts are actually used.

## Teaching loop

Use this loop before moving between major stages such as diagnosis -> design -> implementation -> verification -> impact.

1. **Orient**: summarize the stage in 2-4 sentences.
2. **Elicit**: ask the human to restate what they think is happening.
3. **Diagnose gaps**: compare their restatement against the checklist.
4. **Teach**: fill gaps with the smallest useful explanation.
5. **Drill why**: ask at least one deeper "why" when motivation is shallow.
6. **Quiz**: ask 1-3 questions; mix open-ended and multiple-choice when useful.
7. **Confirm mastery**: mark checklist items only when demonstrated.
8. **Proceed or repeat**: move on only when the current stage is understood.

## What to teach

### Problem

Cover:

- What symptom or need triggered the work.
- Why it existed in the current system or process.
- Which branches, flows, roles, files, states, or conditions matter.
- Which assumptions were confirmed by evidence and which remained unknown.

Good prompt:

```text
Before I explain, can you restate what you think the problem is and why it happens?
```

### Solution

Cover:

- What changed or will change.
- Why this solution is the smallest sufficient fix.
- What alternatives were rejected and why.
- What design decisions, business rules, and edge cases matter.
- How verification proves the intended behavior.

Good prompt:

```text
Can you explain why this solution handles the main path and the edge case separately?
```

### Broader context

Cover:

- Why the change matters to users, maintainers, or product direction.
- What downstream systems, docs, tests, workflows, or teams may be impacted.
- What risks remain and what future checks would catch regressions.

Good prompt:

```text
What would break or become confusing if we shipped this without the change?
```

## Quiz rules

- Prefer open-ended questions for mastery.
- Use multiple-choice when checking a specific distinction.
- Change the position of the correct answer across multiple-choice questions.
- Do not include the answer key until after the human responds.
- Ask the human to explain their reasoning, not only pick an option.
- If the answer is partially correct, acknowledge the correct part, fill the gap, and ask a follow-up.

Multiple-choice format:

```markdown
Question: Why did the bug only appear in [condition]?

A. [plausible wrong answer]
B. [correct answer]
C. [plausible wrong answer]

Pick one and explain your reasoning.
```

## Code and debugger use

Show code, diffs, logs, tests, or debugger steps when explanation alone is too abstract.

Use code/debugger evidence when:

- the bug depends on branching logic;
- a business rule is encoded across multiple files;
- the human misunderstands control flow or data flow;
- edge cases are easier to see through a failing test or breakpoint.

Keep examples focused. Do not paste large files when a file path, function name, or short excerpt is enough.

## Mastery standard

The human has mastered a stage when they can, in their own words:

- state what is happening;
- explain why it happens;
- describe how the solution addresses it;
- reason through at least one edge case;
- explain why the change matters beyond the immediate patch;
- identify whether spec, plan, tasks, verification, and code still align when those artifacts exist.

If the user asks for ELI5, ELI14, or intern-level explanation, adapt the explanation level but keep the same mastery standard.

## Completion rule

Do not mark the teaching goal complete until the checklist shows demonstrated understanding for problem, solution, and broader context.

If the user wants to stop before mastery, record:

```markdown
Status: STOPPED BY USER
Remaining understanding gaps:
- ...
```
