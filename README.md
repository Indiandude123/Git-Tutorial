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


Working with github:
`git remote add origin <repository url>` -> your local git will get the address of the remote repo
`git push origin master/main` -> sends the local repo to the origin


Merge conflict happened on github also:

To merge your `master` branch (which has commits) into the existing but empty `main` branch on GitHub, follow these steps:

### Step 1: Update your local repository
First, ensure your local repository is up-to-date with GitHub:

```bash
git fetch origin
```

### Step 2: Switch to the `main` branch locally
Switch to the existing `main` branch (it already exists remotely):

```bash
git checkout main
```

If you don't have a local copy of the `main` branch yet, create it and track the remote one:

```bash
git checkout -b main origin/main
```

### Step 3: Merge the `master` branch into `main`
Now, merge your local `master` branch into your currently checked-out `main` branch:

```bash
git merge master
```

If Git indicates that there are unrelated histories (which can happen if the branches have no common commits), use this command instead:

```bash
git merge master --allow-unrelated-histories
```

This will merge all commits from `master` into the empty `main`.
And this then created a vim editor. you just hgave to do:
You're currently in Vim, which Git opened to let you write a merge commit message. To complete the merge and exit Vim, do the following:

### Step-by-step:

1. **Press `ESC`** (to ensure you're in normal mode).

2. Type exactly:
```vim
:wq
```

Then press **Enter**.

This command (`:wq`) means "write (save) and quit."

After doing this, Vim will close, and your merge will be completed.

### Step 4: Push merged changes to GitHub
Finally, push the merged changes back to GitHub's `main` branch:

```bash
git push origin main
```

### Optional Step: Delete the redundant `master` branch (if desired)
After merging successfully, you might want to remove the redundant `master` branch from GitHub and locally.

- To delete remotely:

```bash
git push origin --delete master
```

- To delete locally:

```bash
git branch -d master
```

Now your repository will have a single consistent default branch (`main`) with all your commits merged from your previous `master` branch[1][2][7].
