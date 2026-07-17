# Git Cheat Sheet

A quick-reference guide for Git version control.

## Safe & Common Commands

### 1. Check Status and History
```bash
# View the status of your working directory (tracked/untracked files)
git status

# View commit history (compact one-line format)
git log --oneline --graph --all
```

### 2. Stage and Commit Changes
```bash
# Stage a specific file
git add filename.js

# Stage all changes in the current directory
git add .

# Commit staged changes with a descriptive message (following Conventional Commits style)
git commit -m "feat: add user authentication layout"
```

### 3. Push and Pull
```bash
# Pull the latest changes from the remote main branch and merge them
git pull origin main

# Push your local commits to the remote repository
git push origin main
```

---

## ⚠️ Destructive Commands (Use with Caution)

> [!CAUTION]
> The following commands modify or delete commit history and local changes. Double-check your branch and state before executing.

### 1. Hard Reset (Discard Local Changes)
```bash
# Completely discards all uncommitted local changes and reverts to the last commit
git reset --hard HEAD

# Reverts working directory to a specific commit (discards all changes after it)
git reset --hard <commit-hash>
```
*Why it's dangerous:* Any uncommitted changes or reset commits are permanently deleted from your working tree and cannot be recovered easily.

### 2. Force Push (Overwrite Remote History)
```bash
# Overwrites the remote branch with your local branch history
git push origin main --force
```
*Why it's dangerous:* If team members have pushed commits to the remote branch, force pushing will erase their history. Use `git push --force-with-lease` as a safer alternative.

---

## Authoritative Documentation
- [Git Official Documentation](https://git-scm.com/doc)
- [GitHub Docs: Getting Started with Git](https://docs.github.com/en/get-started/using-git)
