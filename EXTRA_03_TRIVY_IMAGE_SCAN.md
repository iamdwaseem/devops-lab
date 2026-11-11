# Extra Topic 3 — Docker Image Security Scanning Using Trivy

**Aim:** Scan a container image for known vulnerabilities.

Install Trivy using the installation method for your operating system, then run:

```bash
docker build -t devops-app .
trivy image devops-app
```

Limit output to important severities:

```bash
trivy image --severity HIGH,CRITICAL devops-app
```

Scan filesystem/dependencies:

```bash
trivy fs .
```

**Interpretation:** Review vulnerability ID, package, installed version, fixed version and severity. Update vulnerable base images/packages, rebuild and scan again.

**Expected:** Trivy prints a vulnerability table; a clean image may show no findings, while vulnerable images show detected issues.

**Viva:** Trivy is a vulnerability scanner; CVE is a public vulnerability identifier; severity indicates risk level; image scanning inspects OS packages and application dependencies.
