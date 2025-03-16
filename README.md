# Git and GitHub

These are what I have learnt by following the playlist by Vikash Das
https://youtube.com/playlist?list=PLupK5DK91flV45dkPXyGViMLtHadRr6sp&feature=shared


## Introduction
Git is a **Version Control System (VCS)** or a **Source Code Manager (SCM)** that helps in tracking changes, collaborating with others, and managing non-linear development efficiently.

## Stages in Git
1. **Workspace**: This is where you work in your local directory. Files here are untracked by Git until added to the staging area.
2. **Staging Area**: The place where files are prepared for a commit. Files move from here to the local repository.
3. **Local Repository**: A version-controlled repository on your local machine where you can track and revert to previous versions.
4. **Remote Repository**: A repository hosted on platforms like GitHub, GitLab, or Bitbucket for collaboration and backup.

## Essential Git Commands

### Viewing Commit History
- `git log` → Shows all the commits made in the repository.
- `git log --oneline` → Displays commit history in a compact format (SHA ID + commit message). This is the most readable version.
- `git log --stat` → Provides detailed commit history, including file changes.
- `git log --oneline --all --graph` → Visual representation of the commit structure across branches.

### Understanding Commits
- **HEAD** → Points to the most recent commit on the current branch.
- **SHA ID** → A unique identifier for each commit, allowing you to navigate between versions.
- `git show <sha_id>` → Displays the code snapshot of a specific commit.

### Viewing Changes
- `git diff` → Shows changes made in the staging area.
  - `a/filename` → After changes
  - `b/filename` → Before changes

### Branching & Navigating Versions
- `git checkout <sha_id>` → Switch to a specific commit.
- `git checkout master` → Return to the master/main branch.
- `git branch` → Lists all branches, with an asterisk (*) indicating the current branch.
- `git branch <branch_name> <sha_id>` → Creates a new branch from a specific commit.
- `git branch -d <branch_name>` → Deletes a branch (only if merged with master/main).
- `git branch -D <branch_name>` → Forcefully deletes a branch (even if not merged, but you must be on a different branch while deleting).

### Merging & Resolving Conflicts
To merge a branch into the main branch:
```sh
 git merge <branch_name>
```
If both branches have modified the same part of a file, a **merge conflict** occurs:

1. Git will display a conflict message:
   ```
   CONFLICT (content): Merge conflict in helper.py
   Automatic merge failed; fix conflicts and then commit the result.
   ```
2. Manually resolve the conflict by choosing the appropriate changes.
3. Stage and commit the resolved version:
   ```sh
   git add helper.py
   git commit -m "Resolved merge conflict"
   ```


## Connecting Local Repository to GitHub

- Add the remote repository URL to your local Git repository:
  ```bash
  git remote add origin <repository_url>
  ```
- Push local changes to GitHub:
  ```bash
  git push origin master  # or main, depending on your default branch
  ```

---

## Handling Merge Conflicts on GitHub

When merging `master` (which has commits) into an existing but empty `main` branch on GitHub, follow these steps:

### Step 1: Fetch the latest updates from GitHub
```bash
 git fetch origin
```

### Step 2: Switch to the `main` branch locally
```bash
 git checkout main
```
If `main` doesn't exist locally, create and track it:
```bash
 git checkout -b main origin/main
```

### Step 3: Merge `master` into `main`
```bash
 git merge master
```
If there are unrelated histories, use:
```bash
 git merge master --allow-unrelated-histories
```

### Step 4: Resolving Merge Conflict in Vim
If a conflict occurs, Git may open Vim for commit message editing. To resolve:
1. **Press `ESC`** (ensure you're in normal mode).
2. Type:
   ```vim
   :wq
   ```
   (This writes and quits Vim.)
3. Complete the merge and commit the changes.

### Step 5: Push Merged Changes to GitHub
```bash
 git push origin main
```

### Step 6 (Optional): Delete the `master` branch
If `master` is redundant:
- **Delete from GitHub:**
  ```bash
  git push origin --delete master
  ```
- **Delete locally:**
  ```bash
  git branch -d master
  ```

Now, `main` becomes the default and only branch.

---

## Cloning a GitHub Repository

- To download a remote repository to your local machine. This creates a new folder on the local machine:
  ```bash
  git clone <repo_url>
  ```

## Pulling from a remote repository
- To fetch and merge the latest changes from `main` into the local branch
  ```bash
  git pull origin main
  ```

### Difference Between `git clone` and `git pull`
| Aspect | `git clone` | `git pull` |
|--------|------------|------------|
| **Purpose** | Creates a new local copy of an existing remote repository. | Updates an existing local repository with the latest changes from remote. |
| **When to use** | When you don't yet have the repository locally. | When you already have the repository locally and want to sync the latest changes. |
| **Frequency** | Typically done only once per repository (initial setup). | Done regularly to keep your local repository up to date. |
| **Effect** | Downloads entire repository history, branches, and tags. | Fetches latest commits from remote and merges them into your current branch. |
| **Syntax Example** | `git clone <repo_url>` | `git pull origin <branch>` |

Use **clone** for the initial download and **pull** regularly to keep your local repository updated.


## Software Versions and Tagging
To create a version tag for a specific commit:
```bash
git tag -a v1.0.0 <sha_id>
```
Git will open Vim to enter a tag annotation message.

### Steps to Enter a Tag Message in Vim
1. Press `i` to enter **insert mode**.
2. Type your tag message (e.g., "First stable release").
3. Press `ESC`, then type `:wq` and press **Enter** to save and exit.

Example tag message:
```
Release version 1.0.0
```

### Push Tags to GitHub
```bash
git push origin v1.0.0
```

