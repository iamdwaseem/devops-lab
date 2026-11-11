# Experiment 12 — Monitoring and Logging Dashboard Integration

**Aim:** Observe application/container health and logs.

## Docker monitoring

```bash
docker ps
docker stats
docker logs -f devops-web-container
```

## Kubernetes monitoring

```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

## Optional Winston application logging (from the other uploaded record)

Install:

```bash
npm install winston
```

Add to `server.js`:

```javascript
const winston = require('winston');

const logger = winston.createLogger({
  level: 'info',
  format: winston.format.combine(
    winston.format.timestamp(),
    winston.format.json()
  ),
  transports: [
    new winston.transports.Console(),
    new winston.transports.File({ filename: 'logs/app.log' })
  ]
});

logger.info('Server started');
```

Create the `logs` directory before starting the application, or configure the file transport/path appropriately.

**Expected observations:** `docker stats` shows CPU, memory, network and block-I/O usage. Docker/Kubernetes logs show application messages. `kubectl describe` shows Pod details and events.

**Result:** Container/application monitoring and logging performed.

**Viva:** Monitoring measures system health/performance; logging records events; CPU and memory are resource metrics; logs help diagnose errors.
