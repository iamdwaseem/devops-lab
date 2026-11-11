# Experiment 8 — Integrate Docker and Kubernetes

**Aim:** Deploy a Dockerized application using Kubernetes Deployment and Service.

Build image:

```bash
docker build -t devops-web .
docker images
```

`deployment.yaml`:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: devops-app
spec:
  replicas: 1
  selector:
    matchLabels:
      app: devops-app
  template:
    metadata:
      labels:
        app: devops-app
    spec:
      containers:
        - name: devops-container
          image: devops-web:latest
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 3000
```

`service.yaml`:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: devops-service
spec:
  type: NodePort
  selector:
    app: devops-app
  ports:
    - port: 80
      targetPort: 3000
```

Apply and verify:

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods
kubectl get deployments
kubectl get services
```

For local clusters, ensure the image is available to the cluster runtime. With Docker Desktop Kubernetes this may be available directly; otherwise load/import the image as required by the cluster.

**Expected:** Deployment READY 1/1, Pod Running, Service created.

**Result:** Dockerized application deployed and exposed through Kubernetes.

**Viva:** Deployment manages replica Pods; Service provides stable networking; NodePort exposes a service through a port on each node.
