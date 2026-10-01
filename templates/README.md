# Examples

This directory is a place for small, practical examples that illustrate the patterns described in the playbook.

Use examples to show how a principle or workflow looks in real code, config, or process snippets.

## Structure

```text
examples/
├── README.md
├── git/
├── testing/
├── api/
├── frontend/
└── deployment/
```

## Example standards

- Keep examples minimal and readable
- Prefer realistic code over synthetic complexity
- Include context that explains what the example is demonstrating
- Update examples when the associated pattern changes

## Suggested example types

- git workflow snippets
- test examples
- HTTP API contracts
- UI patterns
- deployment YAML or pipeline snippets
- database migration examples

---

## Git Commands

### Basic Git Workflow

1. **`git status`** — Shows staged, unstaged, and untracked changes. After your updates, do this first to see what has been updated and is not added yet.

2. **`git add`** — Add or stage files for commit.
   - `git add .` — Add all updated files.
   - `git add "file name"` — Add a specified file.
   - **Undo staging:**
     - `git restore --staged .` — Remove all files from the commit queue.
     - `git restore .` — Discard **all** uncommitted changes in the working directory.
     - `git restore "FileName"` — Restore only the specified file.

3. **`git status`** — Shows staged, unstaged, and untracked changes.

4. **`git commit -m "EnterMessageHere"`** — Commit all staged changes with a message.

5. **`git log`** — Show the commit history and confirm your latest commit.

### Rebase Process

Running a rebase after a commit is a best practice to ensure that your branch is up to date before requesting a pull and merge. This example uses `main`, but you should rebase against your root branch, which could be `main`, `develop`, or another branch as directed by your lead.

```bash
git fetch origin main
git rebase origin/main
```

- **`git fetch origin main`** downloads the latest commits, files, and branch updates from the remote repository named `origin`. It does not change your working files or merge code; it updates your local tracking branches, such as `origin/main`.
- **`git rebase origin/main`** reapplies the commits from your current branch on top of the latest updates from the remote `main` branch. This incorporates the newest changes while maintaining a clean, linear project history.

#### Resolving Rebase Conflicts

If conflicts occur:

1. Click **Edit** and choose the best option, usually **Current**.
2. Under **Results**, edit the file as necessary if you want to keep specific lines from **Incoming**.
3. Review the conflict count and resolve every conflict.
4. Stage each corrected file:

   ```bash
   git add YourFileNameHere
   ```

Continue, skip, or cancel the rebase with:

```bash
git rebase --continue
git rebase --skip
git rebase --abort
```

### Push Process

```bash
git push -u origin YourBranchName
```

This pushes your branch and sets its upstream tracking relationship.

---

## Create a New Branch

> **Best practice:** Always create a new branch from an updated `main` or `develop` branch unless there is a specific reason to branch from another branch. This helps avoid unnecessary merge and rebase conflicts later.

```bash
# Switch to the root branch
git switch main

# Download and merge the latest changes
git pull origin main

# Create and switch to a new branch
git switch -c NewBranchName

# List local branches; the current branch is marked with *
git branch

# Push the new branch and set upstream tracking
git push -u origin NewBranchName
```

### Command Details

1. **`git switch main`** switches to the `main` branch. Start from `main` or `develop` unless you intentionally want your new branch to inherit changes from another branch.
2. **`git pull origin main`** downloads and merges the latest changes from the remote `main` branch, ensuring that your new branch starts from the most current codebase.
3. **`git switch -c NewBranchName`** creates a new branch named `NewBranchName` and automatically switches to it.
4. **`git branch`** lists local branches and confirms which branch you are currently using; it is marked with `*`.
5. **`git push -u origin NewBranchName`** creates the branch in the GitHub repository and sets the upstream tracking relationship. Future pushes can usually use `git push`.

---

## GitFlow vs. Trunk-Based Development

### 1. Trunk-Based Development and GitHub Flow

- **Model:** Everyone branches from and merges back into a single shared branch (`main` / trunk) through short-lived branches, typically lasting 1–3 days.
- **Core characteristic:** No long-lived secondary branches such as `develop` or persistent release branches. Releases deploy directly from `main` or tagged commits.
- **Where it excels:** Modern cloud-native SaaS, CI/CD, microservices, and web applications—such as Azure Static Web Apps and serverless functions—where fast feedback, automated test suites, and continuous delivery are prioritized.
- **Current repository alignment:** This repository uses Trunk-Based Development / GitHub Flow. Feature branches branch from `main`, trigger ephemeral UAT staging slots on pull request, and deploy to production after merging into `main` and passing Three-Party SoD release gates.

### 2. GitFlow

- **Model:** Features branch from and merge into a persistent `develop` branch. Code is promoted in batches from `develop` into `release/*` branches for hardening, then merged into `main` (production) and back-merged into `develop`, with separate `hotfix/*` branches.
- **Core characteristic:** Multiple long-lived parallel branches (`main`, `develop`, `release/*`, and `support/*`).
- **Where it excels:** Traditional packaged software, mobile apps with scheduled app-store releases, embedded firmware, or enterprise systems with rigid quarterly release cadences.
- **Trade-off:** Higher merge-conflict overhead and slower cycle times due to long-lived branch drift.

In classical GitFlow, originally introduced by Vincent Driessen, the repository is built around two permanent, infinite-lifetime branches, supplemented by three types of temporary supporting branches.

#### The Two Core Persistent Branches

##### 1. `main` — Production Branch

- **Role:** Represents authoritative, battle-tested, production-ready code.
- **Rules:**
  - The HEAD of `main` must always reflect the code running in production.
  - Zero active development happens here. Developers never push commits directly to `main`.
  - Commits land on `main` only through formal merges from a `release/*` or `hotfix/*` branch.
  - Every merge into `main` is tagged with a semantic version number, such as `v1.0.0` or `v1.1.0`, to provide an immutable release history and rollback targets.

##### 2. `develop` — Integration / Staging Branch

- **Role:** The day-to-day integration branch for the next release cycle.
- **Rules:**
  - Contains completed features that have passed code review and unit tests and are awaiting inclusion in the next milestone or release candidate.
  - Serves as the base branch from which all `feature/*` branches originate and where they are merged back.
  - Nightly builds, integration test suites, and internal QA environments typically deploy automatically from `develop`.

In short, in GitFlow, `develop` is essentially pre-production staging where finished features are assembled to prepare for release, while active development remains isolated on temporary branches.

#### Supporting Branches

While `main` and `develop` never close, GitFlow uses three temporary branch types that interact with them:

| Branch type | Branches from | Merges back into | Purpose and lifetime |
|---|---|---|---|
| `feature/*` | `develop` | `develop` | **Feature development:** Scoped to a single story or task, such as `feature/SCRUM-65-postgres-setup`. Delete immediately after the pull request is merged into `develop`. |
| `release/*` | `develop` | `main` and `develop` | **Hardening and release preparation:** Cut when `develop` reaches milestone feature freeze, such as `release/v2.1.0`. Used strictly for bug fixes, metadata or version bumps, and final user acceptance testing (UAT). Once verified, merge into `main` with a version tag and back into `develop` so bug fixes are preserved, then delete the branch. |
| `hotfix/*` | `main` | `main` and `develop` | **Emergency production patching:** Cut directly from `main` to address critical production incidents, such as `hotfix/v1.0.1-auth-bypass`. This bypasses `develop` for immediate production deployment. Once verified, merge into `main` with a patch-version tag and into `develop` so the fix is not lost, then delete the branch. |

#### Branch Sequences and Flow

**Feature branch sequence:**

- Cut from `develop`.
- Merge into `develop`.
- Never merge directly into `main`.

**Hotfix branch sequence:**

- Cut from `main`.
- Merge into both `main` and `develop`.
- Bypass `develop` initially so the branch contains only the emergency fix and remains isolated from unreleased work in progress.

**Flow to active features:**

Once the hotfix merges into `develop`, developers working on ongoing `feature/*` branches pull or rebase from `develop` so their branches inherit the hotfix before the next release:

```bash
git merge develop
# or
git rebase develop
```
