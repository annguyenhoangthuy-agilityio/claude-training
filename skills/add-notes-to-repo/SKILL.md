---
name: add-notes-to-repo
description: Add a learning note (training module or course) to the claude-training GitHub repo through a pull request, and update the learning log. Use when the user asks to add, push or save notes to the repo, e.g. "add notes Day 02", "push today's Claude 101 notes".
---

# Add notes to repo

Put the user's learning notes into the `annguyenhoangthuy-agilityio/claude-training` repo in the right place, following the repo conventions, and open a pull request for the user to review and merge.

Follow the repo's `CLAUDE.md` at all times. It takes precedence over this skill.

## Inputs

| Input | Required | Examples |
|---|---|---|
| Note source | Yes | Claude Doc / artifact link, attached file, or pasted text |
| Note type | Yes | Module (`Day 02`) or course (`Claude 101`) |
| Session duration | No | `1h` |
| Status | No | In progress / Done |

If the note type is not given, infer it from the source title (e.g. "AI Fluency Notes" → course `ai-fluency`; "Day 02 – ..." → module `day-02`). If it is still ambiguous, ask before doing anything else.

## Steps

### 1. Read the source

- Claude Doc or claude.ai artifact link: read the doc with the Claude Docs tools and export the relevant tab as Markdown.
- Attached file or pasted text: use it as is.
- Keep the content exactly as written. Do not summarize, rewrite or "improve" it.

### 2. Decide the target file

| Note type | Target file |
|---|---|
| Module | `notes/day-XX.md` (two digits: `day-02`) |
| Course | `notes/course-<course-name>.md` (kebab-case: `course-claude-101.md`) |

### 3. Write the note

Start from the latest `main` (fetch `origin/main`).

**If the target file does not exist:** create it with this header, then the note content:

```markdown
# <Module or course title>

| Field | Value |
|---|---|
| Planned date | |
| Actual sessions | YYYY-MM-DD (<duration>) |
| Status | In progress |
| Blockers | |
```

For course notes exported from a doc that already has its own title, keep the doc's title as the `#` heading and put the header table right below it.

**If the target file already exists:**
- If the new source is an updated version of the same document (it contains the existing content), replace the note body with the new version. Keep the header table, and add today's date to `Actual sessions`.
- Otherwise, append the new content under a heading `## Session YYYY-MM-DD`, and add today's date to `Actual sessions`.
- If the existing file and the new note look unrelated (different topic or module), stop and ask.

### 4. Update the learning log

Append one line to `notes/learning-log.md`:

```
- YYYY-MM-DD – <Module or course> (<duration>): <one-sentence summary of what was covered>
```

Omit `(<duration>)` if not given. The summary is the only text you write yourself; keep it factual and short.

### 5. Update PROGRESS.md

- Fill `Actual start` for the module or course if empty, and set status to 🔄 In progress.
- Set ✅ Done and `Actual done` **only** if the user says it is done in this request.
- Update `**Last updated:**` to today.

### 6. Branch, commit, push

- Branch: `claude/notes-<module-or-course>` (e.g. `claude/notes-day-02`, `claude/notes-claude-101`).
- If an open PR already exists for that branch, push the new commit to the same branch so the existing PR is updated. Do not open a second PR for the same note.
- Commit message: `notes: add <module or course> notes` (or `notes: update <module or course> notes` for an existing file).

### 7. Open the pull request

- **Title:** `Add <module or course> notes` / `Update <module or course> notes`
- **Description:**

```markdown
## What
- <files added or changed>

## Why
Learning notes for <module or course>, session YYYY-MM-DD.

## Review notes
- <items from the checks below, or "None">
```

Never merge, approve or enable auto-merge.

### 8. Report back

In chat, reply briefly with: the PR link, the files changed, and the review notes. Remind the user to click **Delete branch** after merging.

## Checks to include in review notes

- Gaps in numbering (e.g. Lesson 7 missing between 6 and 8)
- Possibly sensitive content: client or company names, real project data, personal data, credentials
- Content that duplicates another note in the repo
- Bylines, mentions or dates in the source that may not belong to the user

## Stop and ask when

- The source cannot be read (broken link, no access, empty)
- The module or course cannot be determined
- The target file exists and looks unrelated to the new note
- The note appears to contain confidential or unsanitized project information

## Out of scope

- Summarizing, translating or rewriting the note
- Exercises, skills, templates and capstone material
- Merging PRs or changing repository settings
