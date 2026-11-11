# DevOps Lab Complete Practical Pack

This pack contains:
- **13 practical files** consolidated from the two uploaded DevOps lab records.
- **6 additional/out-of-syllabus topic files** based on the six topics discussed earlier.
- A quick viva sheet and command revision sheet.

## Source fidelity
The uploaded records contain some overlapping experiments and slightly different implementations. Where they differ, the relevant experiment file labels the version/source so the code is not silently mixed. The six extra topics are concise study implementations, not claimed to be verbatim experiments from the uploaded records.

## Practical index

| File | Practical |
|---|---|
| 01 | Student CRUD REST API using Node.js + Express |
| 02 | Git and GitHub commands |
| 03 | Docker commands and container management |
| 04 | Containerize Node.js CRUD application |
| 05 | Source-code management on GitHub |
| 06 | GitHub Actions environment exploration |
| 07 | CI workflow with GitHub Actions |
| 08 | Docker + Kubernetes Deployment and Service |
| 09 | Manual REST API testing with Postman |
| 10 | Automated API testing (Node fetch/assert; Jest/Supertest; Pytest/JUnit quick alternatives) |
| 11 | Kubernetes automation, scaling and self-healing |
| 12 | Monitoring, logging and Winston |
| 13 | Terraform configuration and local-file lifecycle |

## Six additional topics
1. End-to-end Flask CI/CD using GitHub Actions, tests and Docker
2. DevSecOps source-code analysis and remediation
3. Trivy Docker image security scanning
4. Terraform configuration execution and state management
5. GitOps with Argo CD
6. Kubernetes manifests and deployment

## Before running
- Replace placeholders such as `<username>`, `<repo>`, `<pod-name>` and image names as appropriate.
- Kubernetes local-image examples require the image to be available to the cluster runtime.
- Do not run destructive cleanup commands against resources you need.
- For the Express API examples, start the server in one terminal and run tests/requests in another.
