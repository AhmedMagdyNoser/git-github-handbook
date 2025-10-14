# Git Handbook

**Git** is a version control system that lets you manage and keep track of source code history. It’s used for tracking code changes, tracking who made changes, and coding collaboration.

**GitHub** is a cloud-based hosting service that provides tools to manage Git repositories, enabling developers to collaborate online.

## Getting Started

1. Download and install Git from [https://git-scm.com](https://git-scm.com)
2. Check installation: `git --version`
3. Configure your identity:

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "Your Email"
   ```

## Creating Git Repository

Navigate to your project directory and run:

```bash
git init
```

Git will now start tracking the folder and create a hidden `.git` directory to keep track of changes.

## Repository Status

Check the status of your repository:

```bash
git status
```

**File States:**

- **Tracked** — Files that Git knows about and are part of the repository.
- **Untracked** — Files in your working directory but not yet added to the repository.

**Status Options:**

```bash
git status --short
```

**Status Indicators:**

- `??` - Untracked files
- `A` - Added to stage
- `M` - Modified
- `D` - Deleted

## Git Staging

Staged files are ready to be committed to the repository.

**Adding Files to Stage:**

```bash
git add index.html   # Add specific file
git add --all        # Add all files
git add .            # Add all files in current directory
```

## Git Commit

Commits are snapshots of your project’s history. Each commit saves your progress so you can return to it later if needed.

Commits keep track of progress and changes.
Each commit is a **SAVE POINT** you can return to later.

```bash
git commit -m "Create the first release of Hello World!"
```

**View Commit History:**

```bash
git log
git log --oneline
```

### Git Amend

The **`git commit --amend`** command is used to **modify the most recent commit**.
It combines the current staged changes with the last commit - useful if you forgot to include a file or want to edit the commit message.

**Example:**

```bash
git commit -m "Update README.md"
# Oops! Forgot to add a file
git add new-file.txt
git commit --amend
```

Git will open your default editor, allowing you to change the commit message or confirm it.

**Tip:**
Avoid amending commits that were already pushed to a shared repository — it rewrites history.

## Git Branches

A **Git branch** is a separate line of development that lets you work on new features or fixes without affecting the main project (the **master** branch). You can make changes safely in your branch, then **merge** it back when ready, keeping your workflow organized and controlled.

**Create a new branch:**

```bash
git branch branch-name
```

**List branches:**

```bash
git branch
```

You’ll see an asterisk (\*) next to the current branch.

**Switch to a branch:**

```bash
git switch branch-name
```

### Merging Branches

1. Switch to the target branch (usually `master`):

   ```bash
   git switch master
   ```

2. Merge the branch:

   ```bash
   git merge adding-images
   ```

3. Delete the merged branch:

   ```bash
   git branch -d adding-images
   ```

**Note:** If conflicts occur during merge, fix them manually in a text editor, then stage and commit the results.

## Git Revert

The **`git revert`** command lets you undo a previous commit by creating a **new commit** that cancels out its changes — without changing your project’s history.

1. First, find the commit you want to undo:

   ```bash
   git log --oneline
   ```

2. Copy the commit hash you want to revert, then run:

   ```bash
   git revert abcd123 # where abcd123 is the commit hash
   ```

3. To undo the **latest commit**, just use:

   ```bash
   git revert HEAD
   ```

**Tip:** `git revert` is safer than `git reset` because it keeps your history clean and doesn’t delete any commits.

## Git Reset

The **`git reset`** command is used to undo changes by moving the current branch to a specific commit. Unlike `git revert`, which creates a **new “undo” commit**, `git reset` actually changes history, it brings the repository back to an earlier state without making a new commit, so it should be used with care.

1. First, find the commit you want to reset to:

   ```bash
   git log --oneline
   ```

2. Copy the commit hash you want to reset to, then run:

   ```bash
   git reset abcd123 # where abcd123 is the commit hash
   ```

3. To move back to a previous commit and **delete all changes** (both staged and unstaged):

   ```bash
   git reset --hard abcd123 # where abcd123 is the commit hash
   ```

⚠️ **Warning**

`git reset` rewrites history, so avoid using it on commits that have already been pushed to a shared repository. For shared projects, prefer using `git revert`, which safely undoes changes without deleting commits.

## Git Ignore

The `.gitignore` file tells Git which files or folders to **ignore** and not track. It’s useful for excluding files like environment variables, build outputs, or dependencies.

Example:

```
node_modules/
dist/
.env
```

You can create it manually in your project root: `new-item .gitignore`

For pattern syntax, check: [W3Schools .gitignore Patterns](https://www.w3schools.com/git/git_ignore.asp)
