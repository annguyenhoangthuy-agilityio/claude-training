# Claude Training

Personal workspace for the company's Claude training program. This repo stores my notes, exercises, custom skills, templates and capstone deliverables.

- **Role:** Project Manager / Business Analyst (occasionally QA)
- **Primary track:** BA
- **Learning mode:** Self-paced (running in parallel with project work) – see [PROGRESS.md](PROGRESS.md)

## Training structure

| Modules | Content |
|---|---|
| Day 01–03 | Shared Fundamentals (BA & QA) |
| Day 04–11 | Shared BA/QA activities + role-specific tracks |
| Day 12–15 | Cross-functional capstone |

Required courses: Claude 101, AI Fluency, AI Capabilities and Limitations.

> "Day 01–15" refer to training **modules**, not calendar dates. Actual study dates are recorded inside each note and in `PROGRESS.md`.

## Repository structure

```
claude-training/
├── README.md            # This file
├── PROGRESS.md          # Planned vs actual tracker
├── notes/               # Notes per module (day-01.md ...) + learning-log.md
├── courses/             # Notes for the required courses
├── exercises/           # One folder per exercise (input / output / prompts)
├── skills/              # Custom Claude skills (one folder each, with SKILL.md)
├── templates/
│   ├── ba/              # User story, ticket, release notes
│   └── qa/              # Test case, test matrix, bug report
├── prompts/
│   ├── ba/              # Reusable BA prompts
│   └── qa/              # Reusable QA prompts
└── capstone/            # Day 12–15 deliverables
```

## Conventions

### Naming
- Lowercase, kebab-case, no spaces or accented characters: `day-04-requirements-analysis`
- Always two-digit module numbers: `day-01`, not `day-1`

### Exercise folder layout
```
exercises/day-04-requirements-analysis/
├── README.md     # Task, approach, reflection
├── input/        # Source materials (sanitized)
├── output/       # Deliverables
└── prompts.md    # Prompts used + what worked / didn't
```

### Branches
| Prefix | Use for | Example |
|---|---|---|
| `setup/` | Repo setup and maintenance | `setup/repo-structure` |
| `day-XX/` | Module notes & exercises | `day-04/requirements-analysis` |
| `skill/` | Creating or updating a skill | `skill/user-story-writer` |
| `capstone/` | Capstone work | `capstone/test-plan` |

### Commit messages
Format: `<type>: <short description>`

| Type | Use for | Example |
|---|---|---|
| `notes` | Learning notes | `notes: add day-02 learnings on projects` |
| `exercise` | Exercises | `exercise: complete day-04 user stories` |
| `skill` | Skills | `skill: add release-notes-generator` |
| `template` | Templates | `template: update bug report format` |
| `docs` | README, PROGRESS, repo docs | `docs: update progress to day 05` |

## Workflow
1. `git checkout main && git pull`
2. `git checkout -b <prefix>/<name>`
3. Work, then `git add` + `git commit`
4. `git push -u origin <branch>`
5. Open a pull request, review **Files changed**, merge
6. `git checkout main && git pull && git branch -d <branch>`

## Data handling
Real project materials used in exercises must be sanitized: no client names, credentials, personal data or confidential business information.
