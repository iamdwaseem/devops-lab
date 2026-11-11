# Last-Minute DevOps Viva and Commands

## Definitions
- DevOps: practices that combine development and operations to deliver software reliably.
- Git: distributed version control.
- Docker: containerization platform.
- Image: template used to create containers.
- Container: isolated running instance of an image.
- Kubernetes: container orchestration platform.
- Pod: smallest deployable Kubernetes unit.
- Deployment: manages replicas and rollout of Pods.
- Service: stable network endpoint for Pods.
- CI: Continuous Integration.
- CD: Continuous Delivery/Deployment.
- Workflow: automated process in GitHub Actions.
- Runner: machine that executes workflow jobs.
- Pytest: Python testing framework.
- JUnit: Java testing framework.
- Jest: JavaScript testing framework.
- Assertion: checks expected versus actual result.
- Terraform: Infrastructure as Code tool.
- Provider: plugin used by Terraform to interact with a platform.
- Resource: object managed by Terraform.
- State: tracks managed infrastructure.
- GitOps: Git is the source of truth for desired infrastructure/application state.
- Argo CD: GitOps continuous-delivery tool for Kubernetes.
- Trivy: vulnerability scanner for images, filesystems and repositories.
- DevSecOps: integrates security throughout the software lifecycle.
- Monitoring: observes health and performance.
- Logging: records application/system events.

## Command sheet

### Git
```bash
git status
git add .
git commit -m "message"
git log --oneline
git branch
git switch -c feature
git push
git pull
```

### Docker
```bash
docker --version
docker pull nginx
docker images
docker build -t app .
docker run -d --name web -p 8080:80 nginx
docker ps
docker ps -a
docker logs web
docker stats
docker stop web
docker rm web
```

### Kubernetes
```bash
kubectl get nodes
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deployments
kubectl get pods
kubectl get services
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl scale deployment <name> --replicas=3
kubectl delete pod <pod-name>
```

### Terraform
```bash
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
terraform show
terraform state list
terraform state show <resource-address>
terraform destroy
```

### Testing / CI
```bash
pytest -v
mvn test
npm test
node test_cases.js
git push
```

### Security
```bash
trivy image <image-name>
trivy fs .
bandit -r .
```
