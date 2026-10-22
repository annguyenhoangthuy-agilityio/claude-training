# Day 02 — Prompts

The prompts below are copied from `output/day-02-ticket-analysis.md`.

## Exercise 1 — Ticket analysis

Prompt 1 (SS-201):

```text
You are a senior developer reviewing a feature ticket before implementation.
Ticket: SS-201 in the backlog @https://claude.ai/artifact/Amu78xhgZQQewDVvL1LfE5

Do two things:

1. Answer these 3 questions, 1–2 sentences each:
   - What it asks: the core scope of the ticket.
   - What's ambiguous: the most important unclear or missing points
     (e.g. business rules, validation, error handling, security, UI states).
   - First step: what the developer should do first to start implementation.

2. Draft clarifying questions for the ticket author based on the gaps above.
   - Maximum 5 questions, each under 30 words.
   - Order them by impact: questions that block implementation come first.
   - Only ask what the ticket doesn't already answer; fewer than 5 is fine.

Output format:
## Summary
**What it asks:** ...
**What's ambiguous:** ...
**First step:** ...

## Clarifying questions
1. ...
```

Prompt 2 (SS-202 to SS-205):

```text
continue to review ticket SS-202, SS-203, SS-204, SS-205 following to the outline above
```

## Exercise 2 — Reproduce and understand

```text
You are a QA. Rewrite the bug ticket below so a developer can reproduce the bug.

Bug ticket SS-206 in the training backlog

Tasks:
Rewrite the ticket with these sections:
   - Title: [Area] short description of the wrong behavior
   - Environment & setup: OS/browser
   - Preconditions: starting state, account/role, test data
   - Steps to reproduce: numbered, one action per step, concrete data
   - Expected result
   - Actual result
   - Frequency: always / intermittent
```

## What worked / didn't

To be added.
