# Git Guideline

A practical Git reference for BA/QA work. It covers the standard workflow (branch → commit → push → pull request → merge), the commands needed at each step, and additional commands that are useful for reviewing changes, writing release notes and investigating issues.

Commands are written for a macOS/Linux terminal (or Git Bash on Windows). Replace placeholders in angle brackets, e.g. `<branch>`, with your own values.

---

## 1. Core concepts

A change moves through four places:

```
Working directory  --git add-->  Staging area  --git commit-->  Local repo  --git push-->  Remote (GitHub)
(files you edit)                 (what will be committed)        (history on your machine)    (origin)
```

| Term | Meaning | BA/PM analogy |
|---|---|---|
| **Repository (repo)** | A project folder whose full history is tracked by Git | A document library with version history |
| **Commit** | A saved snapshot of changes, with a message | A versioned revision of a document |
| **Branch** | A separate line of work; keeps `main` clean | A draft copy of an approved requirement |
| **`main`** | The main, "approved" branch | The baseline / signed-off version |
| **Remote / `origin`** | The copy of the repo on GitHub | The shared drive everyone reads from |
| **Pull request (PR)** | A request to merge a branch into `main`, with review | A review & sign-off step |
| **Merge** | Combining a branch into `main` | Incorporating approved changes into the baseline |
| **HEAD** | The commit you are currently on | "Where I am now" |

---

## 2. Standard workflow: branch → commit → push → PR → merge

### Step 0 – Check where you are

```bash
cd <path-to-repo>
git status
git remote -v
```

| Command | What it does |
|---|---|
| `cd <folder>` | Move into the repo folder |
| `ls -la` | List all files including hidden ones; use it to check for the `.git` folder |
| `git status` | Show the current branch and changed files. Run it whenever you are unsure |
| `git remote -v` | Show which GitHub repo this local repo is linked to |
| `git config user.name` / `git config user.email` | Show the name/email attached to your commits |

Expected:
```
On branch main
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean
```

### Step 1 – Update `main` and create a branch

```bash
git checkout main
git pull
git checkout -b day-01/fundamentals
```

| Command | What it does |
|---|---|
| `git checkout main` | Switch to the `main` branch |
| `git pull` | Download the latest changes from GitHub. Always do this before creating a branch |
| `git checkout -b <branch>` | Create a new branch (`-b`) and switch to it |

### Step 2 – Make changes

Create or edit files, then **save them** (Cmd + S). Useful commands:

| Command | What it does |
|---|---|
| `mkdir -p <folder>/<subfolder>` | Create folders, including nested ones |
| `touch <file>` | Create an empty file |
| `touch <folder>/.gitkeep` | Placeholder so an empty folder is tracked (Git ignores empty folders) |
| `open -a TextEdit <file>` | Open a file **inside the repo** with TextEdit (use Format → Make Plain Text for Markdown) |
| `code <file>` | Open a file with VS Code (if installed) |
| `git mv <old> <new>` | Move or rename a file and keep its history |
| `git rm <file>` / `git rm -r <folder>` | Delete a file/folder and stage the deletion in one step |

### Step 3 – Stage and commit

```bash
git status
git add .
git status
git commit -m "notes: add day-01 learnings"
```

| Command | What it does |
|---|---|
| `git status` (before add) | Changed files appear **red** = not staged |
| `git add .` | Stage **all** changes |
| `git add <file1> <file2>` | Stage specific files only (preferred when you changed unrelated things) |
| `git status` (after add) | Staged files appear **green** = ready to commit. Check nothing unexpected is included |
| `git commit -m "<message>"` | Save a snapshot to local history with a message |

### Step 4 – Push to GitHub

```bash
git push -u origin day-01/fundamentals   # first push of a new branch
git push                                 # later pushes on the same branch
```

| Command | What it does |
|---|---|
| `git push -u origin <branch>` | Upload the branch to GitHub; `-u` links local and remote branches |
| `git push` | Upload new commits to the already-linked branch |

Pushing more commits to a branch that already has a PR **updates the PR automatically**.

### Step 5 – Open a pull request (GitHub)

1. Open the link printed by `git push`, or click **Compare & pull request** on the repo page
2. **Title:** short and specific, e.g. `Add Day 01 notes`
3. **Description:** **What** changed and **Why**
4. Click **Create pull request**
5. Review the **Files changed** tab before merging, even for your own PRs

### Step 6 – Merge (GitHub)

1. **Conversation** tab → **Merge pull request** → **Confirm merge**
2. Click **Delete branch**

### Step 7 – Clean up locally

```bash
git checkout main
git pull
git branch -d day-01/fundamentals
```

| Command | What it does |
|---|---|
| `git checkout main` | Go back to `main` |
| `git pull` | Download the merged result |
| `git branch -d <branch>` | Delete the local branch (only works if merged, so it is safe) |
| `git push origin --delete <branch>` | Delete the branch on GitHub, if not done in Step 6 |

---

## 3. Keeping your branch up to date

### `git pull` vs `git pull --rebase`

| Command | What happens | When to use |
|---|---|---|
| `git pull` | Downloads remote changes and **merges** them into your branch; may create an extra "merge commit" | Default, simplest |
| `git pull --rebase` | Downloads remote changes and **replays your local commits on top of them**; history stays linear, no extra merge commit | Your branch is behind the remote and you have local commits not yet pushed |

Example: you committed notes locally, but meanwhile you (or Claude) pushed another commit to the same branch from GitHub. `git push` is rejected:

```
! [rejected]  day-01/fundamentals -> day-01/fundamentals (fetch first)
```

Fix:
```bash
git pull --rebase
git push
```

Rule of thumb: only rebase commits that **have not been pushed** yet, and never rebase `main`.

To make rebase the default for `git pull`:
```bash
git config --global pull.rebase true
```

### Update a feature branch with the latest `main`

```bash
git checkout main
git pull
git checkout day-04/requirements-analysis
git merge main
```

`git merge main` brings new commits from `main` into your branch, so your PR is tested against the latest baseline.

### `git fetch`

```bash
git fetch
git status
```

`git fetch` downloads remote information **without changing your files**. Safe way to see whether you are behind (`Your branch is behind 'origin/main' by 2 commits`).

---

## 4. Reviewing history and changes (most useful for BA/QA)

### `git log` – what happened, when, by whom

| Command | What it shows | BA/QA use |
|---|---|---|
| `git log` | Full commit history (press `q` to exit) | General history |
| `git log --oneline` | One line per commit | Quick overview |
| `git log --oneline --graph --all` | History as a graph, all branches | See how branches were merged |
| `git log -5` | Last 5 commits | Recent activity |
| `git log --since="2 weeks ago"` | Commits in a time window | Sprint review, weekly report |
| `git log --author="An"` | Commits by one person | Track contributions |
| `git log --grep="login"` | Commits whose message contains a word | Find all changes related to a feature or ticket ID |
| `git log -- <file>` | Commits that touched one file | History of one requirement doc |
| `git log -p <file>` | Commits plus the actual changes for one file | See how a requirement evolved |
| `git log v1.0..v1.1 --oneline` | Commits between two tags/versions | **Draft release notes** |

### `git diff` – what exactly changed

| Command | Compares | BA/QA use |
|---|---|---|
| `git diff` | Working directory vs staging (unstaged changes) | Check edits before `git add` |
| `git diff --staged` | Staging vs last commit | Final check before `git commit` |
| `git diff main..day-04/requirements-analysis` | Two branches | Preview what a PR will change |
| `git diff <commit1> <commit2>` | Two commits | Compare two versions |
| `git diff --stat main..<branch>` | Summary: files and number of lines changed | Quick scope check of a change |
| `git diff --word-diff` | Changes word by word instead of line by line | Reviewing prose (requirements, notes) |

Reading diff output: lines starting with `-` (red) were removed, `+` (green) were added.

### Other inspection commands

| Command | What it does | BA/QA use |
|---|---|---|
| `git show <commit>` | Details and changes of one commit | Inspect a specific change referenced in a ticket |
| `git show --stat <commit>` | Files changed in one commit | Scope of a fix |
| `git blame <file>` | Who last changed each line, and in which commit | Find who to ask about a requirement or a line of code |
| `git tag` | List version tags | Know which releases exist |
| `git branch` | List local branches (`*` = current) | Where am I |
| `git branch -a` | List local and remote branches | See all work in progress |

---

## 5. Undoing things

| Situation | Command | Note |
|---|---|---|
| Discard unsaved-to-Git edits in a file | `git restore <file>` | ⚠️ Edits are lost permanently |
| Unstage a file (keep the edits) | `git restore --staged <file>` | Reverses `git add` |
| Fix the last commit message (not pushed yet) | `git commit --amend -m "new message"` | Do not amend commits already pushed |
| Add a forgotten file to the last commit (not pushed yet) | `git add <file>` then `git commit --amend --no-edit` | Same rule as above |
| Undo a commit that is already pushed | `git revert <commit>` | Creates a new commit that reverses it; safe for shared history |
| Temporarily put away unfinished work | `git stash` | Saves changes and cleans the working directory |
| Bring stashed work back | `git stash pop` | |
| See stashed items | `git stash list` | |

`git stash` example: you are mid-way through Day 04 notes and need to switch to `main` urgently.

```bash
git stash
git checkout main
# ... do something ...
git checkout day-04/requirements-analysis
git stash pop
```

---

## 6. Merge conflicts

A conflict happens when the same lines were changed in two places. Git marks them in the file:

```
<<<<<<< HEAD
Status: In progress
=======
Status: Done
>>>>>>> main
```

How to resolve:
1. Open the file and decide the correct content
2. Delete the markers `<<<<<<<`, `=======`, `>>>>>>>`
3. Save, then:
   ```bash
   git add <file>
   git commit            # if you were merging
   git rebase --continue # if you were rebasing
   ```

To cancel instead: `git merge --abort` or `git rebase --abort`.

Like reconciling two reviewers' comments on the same requirement: you pick the final wording, not Git.

---

## 7. Recommended conventions

Check the repo's README first; if it defines its own conventions, follow those.

### Naming
- Lowercase, kebab-case, no spaces or accented characters: `day-04-requirements-analysis`
- Zero-padded numbers so files sort correctly: `day-01`, not `day-1`
- Consistent prefixes to group related files: `course-claude-101.md`, `course-ai-fluency.md`

### Branch prefixes
| Prefix | Use for | Example |
|---|---|---|
| `setup/` | Repo setup and maintenance | `setup/remove-courses-folder` |
| `notes/` | Standalone notes | `notes/git-guideline` |
| `day-XX/` | Module notes and exercises | `day-04/requirements-analysis` |
| `skill/` | Skills | `skill/user-story-writer` |
| `capstone/` | Capstone work | `capstone/test-plan` |

### Commit messages
Format: `<type>: <short description>` – imperative, lowercase, under ~60 characters.

| Type | Example |
|---|---|
| `notes` | `notes: add day-02 learnings on projects` |
| `exercise` | `exercise: complete day-04 user stories` |
| `skill` | `skill: add release-notes-generator` |
| `template` | `template: update bug report format` |
| `docs` | `docs: update progress to day 05` |

### Good habits
- Run `git status` before and after every `add`, `commit`, `checkout`
- `git pull` before creating a branch
- One commit = one clear purpose; the message must match the actual change
- Update docs (README, PROGRESS) in the same PR as the change they describe
- Review **Files changed** before merging
- Never commit secrets, credentials, client names or personal data; sanitize real project material

---

## 8. Troubleshooting

| Message | Cause | Fix |
|---|---|---|
| `fatal: not a git repository` | You are not inside the repo folder (e.g. the outer folder of a nested folder) | `ls -la`, then `cd` into the folder that contains `.git` |
| `nothing to commit, working tree clean` (but you edited files) | File not saved, or saved in another folder | `pwd`, `head -3 <file>`; reopen with `open -a TextEdit <file>`, Cmd + S, `git status` |
| `! [rejected] ... (fetch first)` | Remote branch has commits you don't have | `git pull --rebase`, then `git push` |
| `Your branch is behind 'origin/main'` | Remote has newer commits | `git pull` |
| `error: Your local changes would be overwritten by checkout` | Uncommitted changes block switching branches | Commit them, or `git stash` |
| `error: The branch '<x>' is not fully merged` | Deleting a branch that is not merged | Check the PR was merged; force delete with `git branch -D <x>` only if you are sure |
| Asked for password on `git push` | GitHub no longer accepts account passwords | Use browser sign-in (Git Credential Manager) or a Personal Access Token |
| `.DS_Store` appears in `git status` | macOS system file | Add `.DS_Store` to `.gitignore` |

---

## 9. Cheat sheet

```bash
# Start new work
git checkout main
git pull
git checkout -b <prefix>/<name>

# Save work
git status
git diff
git add <files>      # or: git add .
git diff --staged
git commit -m "<type>: <description>"

# Share work
git push -u origin <prefix>/<name>   # first time
git push                             # afterwards
git pull --rebase                    # if push is rejected

# GitHub: Create PR → review Files changed → Merge → Delete branch

# Clean up
git checkout main
git pull
git branch -d <prefix>/<name>

# Inspect
git log --oneline -10
git log --grep="<keyword>"
git diff --stat main..<branch>
git show <commit>
```
