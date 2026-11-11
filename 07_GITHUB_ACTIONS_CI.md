# Experiment 7 — Continuous Integration Using GitHub Actions

**Aim:** Automatically install dependencies, run tests and build a Docker image after a push.

Add a test script to `package.json` (example for Jest):

```json
{
  "scripts": {
    "test": "jest --runInBand"
  }
}
```

Create `.github/workflows/ci.yml`:

```yaml
name: CI Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: actions/setup-node@v4
        with:
          node-version: 20

      - run: npm install
      - run: npm test
      - run: docker build -t devops-app .
```

## Trigger

```bash
git add .
git commit -m "Add CI pipeline"
git push
```

## Verify
GitHub → Actions. Expected steps: checkout, setup Node, install dependencies, run tests, build image. Workflow should be green if every step succeeds.

**Important:** The uploaded record's simpler variant uses `node --check server.js` as a syntax check; its more complete CI practical runs `npm test` and `docker build`.

**Viva:** CI means Continuous Integration. A CI pipeline automatically checks changes. A failed step makes the workflow fail.
