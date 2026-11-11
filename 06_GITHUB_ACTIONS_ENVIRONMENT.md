# Experiment 6 — GitHub Actions Setup and Environment Exploration

**Aim:** Configure a basic CI environment and inspect the GitHub-hosted runner.

Create `.github/workflows/environment.yml`:

```yaml
name: Environment Exploration

on: [push]

jobs:
  explore:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Show environment
        run: |
          node --version
          npm --version
          pwd
          ls -la

      - name: Install dependencies
        run: npm install
```

## Trigger and verify

```bash
git add .github/workflows/environment.yml
git commit -m "Add environment workflow"
git push
```

Open GitHub → repository → Actions → latest workflow run.

**Expected:** Checkout and Node setup succeed; Node/npm versions and workspace files are printed; dependencies install.

**Result:** GitHub-hosted runner environment explored.

**Viva:** Workflow = automated process; runner = machine executing jobs; action = reusable task; trigger = event that starts workflow.
