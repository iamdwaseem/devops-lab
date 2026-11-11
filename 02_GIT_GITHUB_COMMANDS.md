# Experiment 2 — Git and GitHub Commands

**Aim:** Track project changes locally and push them to GitHub.

## Commands

```bash
git --version
git config --global user.name "Your Name"
git config --global user.email "you@example.com"

git init
git status
git add .
git commit -m "Initial commit"

git branch
git log --oneline

git remote add origin https://github.com/<username>/<repository>.git
git branch -M main
git push -u origin main
```

## Branch workflow

```bash
git switch -c feature
# make changes
git add .
git commit -m "Added feature"
git push -u origin feature

git switch main
git pull origin main
git merge feature
git push
```

## Verify

```bash
git status
git log --oneline
git remote -v
git branch
```

Expected: commit history is shown and the working tree is clean after committing/pushing.

**Result:** Local repository initialized, files committed and remote GitHub repository connected.

**Viva:** Git is a distributed version-control system. GitHub hosts Git repositories. `add` stages changes, `commit` records them, `push` uploads commits, `pull` fetches and integrates remote changes, and a branch isolates work.
