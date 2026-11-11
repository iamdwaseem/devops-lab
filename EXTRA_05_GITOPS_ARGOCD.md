# Extra Topic 5 — GitOps Using Argo CD

**Aim:** Understand GitOps and deploy Kubernetes applications from Git using Argo CD.

## GitOps concept
Git repository stores the desired Kubernetes configuration. Argo CD continuously compares the live cluster with Git and synchronizes differences.

## Basic workflow
1. Store Kubernetes YAML manifests in Git.
2. Install/configure Argo CD in the cluster.
3. Register the Git repository in Argo CD.
4. Create an Argo CD Application pointing to the manifest path.
5. Sync the application.
6. Verify deployment and application health.

## Example Application manifest

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: demo-app
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/<username>/<repo>.git
    targetRevision: HEAD
    path: k8s
  destination:
    server: https://kubernetes.default.svc
    namespace: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
```

Apply (after Argo CD is installed and repository/path are correct):

```bash
kubectl apply -f application.yaml
kubectl get applications -n argocd
```

**Viva:** GitOps uses Git as the source of truth; Argo CD is a declarative continuous-delivery tool for Kubernetes; sync applies desired state; self-heal reconciles drift.
