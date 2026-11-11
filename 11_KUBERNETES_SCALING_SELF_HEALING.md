# Experiment 11 — Automate Running and Scaling Application Using Kubernetes

**Aim:** Run a containerized application with Kubernetes, scale replicas and monitor Pods.

Build image (use the image name in your manifest):

```bash
docker build -t 23071a0523-week7-app .
```

`week7-deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: week7-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: week7-app
  template:
    metadata:
      labels:
        app: week7-app
    spec:
      containers:
        - name: week7-container
          image: 23071a0523-week7-app:latest
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 3000
```

Apply and inspect:

```bash
kubectl apply -f week7-deployment.yaml
kubectl get deployments
kubectl get pods
```

Scale:

```bash
kubectl scale deployment week7-deployment --replicas=3
kubectl get deployment
kubectl get pods
```

Logs:

```bash
kubectl logs <pod-name>
```

Self-healing demonstration:

```bash
kubectl delete pod -l app=week7-app
kubectl get pods
```

Expected: Deployment returns to its desired replica count by creating replacement Pods.

**Result:** Deployment, scaling and Pod monitoring demonstrated.

**Viva:** Replicas are copies of Pods; scaling changes replica count; self-healing restores desired state; `kubectl logs` displays container logs.
