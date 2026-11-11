# Experiment 5 — Source Code Management on GitHub

**Aim:** Upload and manage the backend project using Git and GitHub.

## `.gitignore`

```gitignore
node_modules/
.env
*.log
```

## Commands

```bash
git status
git add .
git commit -m "Add backend CRUD API"
git remote add origin https://github.com/<username>/<repo>.git
git branch -M main
git push -u origin main
```

## Feature branch

```bash
git switch -c api-validation
# make changes
git add .
git commit -m "Add API validation"
git push -u origin api-validation

git switch main
git pull origin main
git merge api-validation
git push
```

**Verify:** Check repository files and commit history on GitHub; run `git status` locally.

**Result:** Project source is version-controlled and pushed to GitHub.

**Viva:** `.gitignore` excludes files from Git tracking; remote is the hosted repository URL; merge combines branch changes.
