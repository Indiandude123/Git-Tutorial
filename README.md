# Git and GitHub

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


