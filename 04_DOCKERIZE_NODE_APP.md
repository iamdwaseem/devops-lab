# Experiment 4 — Containerize a Node.js CRUD Application Using Docker

**Aim:** Package a Node.js/Express application into a Docker image and run it as a container.

## Project files
`server.js`, `package.json`, `Dockerfile`

## Minimal `package.json`

```json
{
  "name": "devops-crud-app",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": { "start": "node server.js" },
  "dependencies": { "express": "^4.21.2" }
}
```

## Minimal `server.js`

```javascript
const express = require('express');
const app = express();
app.use(express.json());

app.get('/', (req, res) => res.send('DevOps Docker Application'));
app.get('/students', (req, res) => res.json([{ id: 1, name: 'Rahul' }]));

app.listen(3000, () => console.log('Application running on 3000'));
```

## `Dockerfile`

```dockerfile
FROM node:20
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```

## Build, run and test

```bash
docker build -t devops-web .
docker images
docker run -d --name devops-web-container -p 8080:3000 devops-web
docker ps
docker logs devops-web-container
```

Open `http://localhost:8080` and expect `DevOps Docker Application`.

## Cleanup

```bash
docker stop devops-web-container
docker rm devops-web-container
```

**Result:** Node.js application image built and container launched successfully.

**Viva:** `FROM` selects the base image; `WORKDIR` sets working directory; `COPY` copies files; `RUN` executes build-time commands; `EXPOSE` documents the container port; `CMD` defines the default command.
