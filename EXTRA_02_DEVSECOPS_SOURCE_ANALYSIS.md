# Extra Topic 2 — DevSecOps Source-Code Analysis and Remediation

**Topic status:** Additional preparation. The earlier discussion identified source analysis, two security issues and recovery/remediation, but did not preserve the exact code snippet or named vulnerabilities. This is a safe illustrative demonstration, not a claim about the exact unseen question.

## Example insecure code

```python
# Insecure: hard-coded secret
API_KEY = "demo-secret-key"

# Insecure: SQL built by string concatenation
query = "SELECT * FROM users WHERE name = '" + user_input + "'"
```

## Issues
1. Hard-coded secret: credentials can leak through source control.
2. SQL injection: untrusted input is concatenated into SQL.

## Remediation

```python
import os
API_KEY = os.environ["API_KEY"]

cursor.execute("SELECT * FROM users WHERE name = ?", (user_input,))
```

## Basic source scan
Use a secret scanner/SAST tool approved for the lab. Example with Bandit for Python:

```bash
pip install bandit
bandit -r .
```

## Recovery actions
- Remove exposed secret from code and rotate/revoke it at the provider.
- Store secrets in environment variables or a secrets manager.
- Replace concatenated SQL with parameterized queries.
- Re-run scanner and tests.
- Review repository history and access logs if a real credential was exposed.

**Viva:** DevSecOps integrates security into development and operations; SAST analyzes source code without running it; secret scanning detects credentials; remediation fixes findings; rotation replaces compromised credentials.
