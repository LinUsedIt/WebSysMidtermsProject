---
name: spec-driven-workflow
description: Use this skill whenever you start the project, draft or update specs/design.md or specs/tasks.md, begin or finish a task or stage, log a decision, or notice the specs and the code disagree. Use it even if the user just says "let's start", "plan this", "what's next", or "continue". Do not start coding before the approval gates in this skill are met.
---

# Spec-Driven Workflow

## Drafting specs/design.md
Inputs: specs/requirements.md, the wireframe, the user's design notes. Line 1: `Status: DRAFT`.
Sections (keep each short):
1. **Pages:** list each page, its purpose, and which wireframe frame it maps to.
2. **File structure:** tree of index.html, other pages, style.css, script.js, /assets/{images,audio,video}.
3. **Design tokens:** colors, font stack, type scale, spacing. Define as CSS variables.
4. **Shared parts:** nav, footer, Technical Media Spec Table (which pages show it).
5. **Interactive features:** for each, one line on what the user does and what changes. Cover the RLE demo, the raster/vector comparison, and the quiz.
6. **Media plan:** every image, SVG, audio file: purpose, source, target format.
7. **Content map:** each place a CONTENT-TODO will go (id + purpose). No actual copy.
8. **Open questions:** anything unresolved. Ask the user before approval.

Stop after drafting. Tell the user to review and set `Status: APPROVED`.

## Drafting specs/tasks.md
Line 1: `Status: DRAFT`. Then a `Current stage:` line. Use this format:

```
## Stage 2: Layout
- [ ] T2.1 Shared nav and footer on every page
  - Covers: R1, R4 | Skills: semantic-html, css-typography
  - Done when: each page has exactly one <nav> and one <footer>
```
Rules:
- Stages in order: Setup, Layout, Typography, Media, Interactivity, Spec Table, QA, Content handoff.
- Every task cites requirement IDs, lists skills, and has a checkable "Done when" (a command or a countable fact).
- Tasks small enough to finish in one go. No task depends on a later one.
- Add a `## Blocked` section at the bottom for open questions.

## Running tasks
1. Read the current task only. Load the skills it lists.
2. Do it. Run the "Done when" check.
3. Pass: tick `[x]`, update `Current stage`. Fail: fix once, recheck, else move to Blocked and ask.
4. End of stage: 3-line report (done / failed / next), then stop for the user.

## Decisions and drift
- When the user settles a conflict, append to specs/decisions.md: `D#: question | decision | date`.
- If code must differ from the spec, change the spec first (propose it), then the code.
- Never edit requirements.md without the user's yes.
