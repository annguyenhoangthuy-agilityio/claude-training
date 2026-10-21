# CLAUDE.md

Rules for Claude when working in this repository. The repo owner reviews and merges all changes; Claude prepares them.

## About this repo

Personal workspace for a Claude training program (BA track, occasionally QA). It holds notes, exercises, custom skills, templates and capstone deliverables. See `README.md` for the structure and conventions, and `PROGRESS.md` for the training tracker.

## Git workflow (required)

1. Start from the latest `main`: fetch and branch from `origin/main`.
2. Work only on a branch prefixed `claude/`, e.g. `claude/add-day-01-notes`. One branch per request.
3. Never push to `main`. Never force-push, rebase or rewrite history on a branch that has an open PR unless the owner asks.
4. Open a pull request for every change, with:
   - **Title:** short and specific
   - **Description:** `## What` (files and changes), `## Why`, and `## Review notes` (anything uncertain, missing or worth checking)
5. Never merge a pull request, approve one, or enable auto-merge. The owner reviews and merges.
6. Never delete branches other than `claude/` branches whose PR has been merged.
7. Never change repository settings, rulesets, collaborators, GitHub Actions or secrets.

`main` is protected by a ruleset (pull request required, no force push, no deletion). Do not try to work around it.

## Scope

- Change only the files needed for the request. If a related improvement seems useful (a typo elsewhere, an outdated README line), mention it in the PR's review notes instead of changing it.
- Do not delete, move or rename the owner's files unless asked. When asked, use `git rm` / `git mv`.
- When a change affects documented structure or conventions, update `README.md` in the same PR.
- Ask before large restructures or anything that would rewrite much of an existing file.

## Content rules

- Preserve the owner's content as written when copying notes in (e.g. exported from a doc). Do not rewrite, summarize or "improve" it unless asked; flag gaps in the PR instead.
- Never commit secrets, credentials, client names, personal data or confidential project information. Material from real projects must be sanitized; if in doubt, ask.
- Write repo content in English unless the owner asks otherwise. Keep technical terms in English.
- Use plain Markdown.

## Conventions

Follow `README.md`. Summary:

- **Names:** lowercase kebab-case, no spaces or accented characters; zero-padded module numbers (`day-01`).
- **Where files go:**
  - Module notes: `notes/day-XX.md`
  - Course notes: `notes/course-<course-name>.md`
  - Exercises: `exercises/day-XX-<topic>/` with `README.md`, `input/`, `output/`, `prompts.md`
  - Skills: `skills/<skill-name>/SKILL.md`
  - Templates: `templates/ba/`, `templates/qa/`
  - Prompts: `prompts/ba/`, `prompts/qa/`
  - Capstone: `capstone/`
- **Commit messages:** `<type>: <short description>`, types `notes`, `exercise`, `skill`, `template`, `docs`. One clear purpose per commit.

## Training content and submissions

- Help the owner learn: for exercises, guide and review rather than producing complete submissions, unless the owner explicitly asks for a full draft.
- Do not mark courses, modules or exercises as done in `PROGRESS.md` unless the owner confirms they are done.
