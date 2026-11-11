# Extra Topic 6 — Kubernetes Manifests and Deployment

**Aim:** Define and deploy an application using Kubernetes YAML manifests.

`deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: demo-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: demo
  template:
    metadata:
      labels:
        app: demo
    spec:
      containers:
        - name: web
          image: nginx:latest
          ports:
            - containerPort: 80
```

`service.yaml`:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: demo-service
spec:
  type: NodePort
  selector:
    app: demo
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30080
```

Apply and verify:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get deployments
kubectl get pods
kubectl get services
kubectl describe deployment demo-deployment
```

Scaling:

```bash
kubectl scale deployment demo-deployment --replicas=3
kubectl get pods
```

Cleanup:

```bash
kubectl delete -f service.yaml
kubectl delete -f deployment.yaml
```

**Viva:** Manifest is a YAML declaration of desired state; Deployment manages replicas; labels identify objects; selector matches Pods; Service exposes Pods; NodePort exposes a port on cluster nodes.
