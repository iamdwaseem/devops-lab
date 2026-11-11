# Experiment 3 — Docker Commands for Container Management

**Aim:** Manage Docker images and containers using basic CLI commands.

## Commands

```bash
docker --version
docker pull nginx
docker images

docker run -d --name web -p 8080:80 nginx
docker ps
docker ps -a

docker logs web
docker inspect web
docker stats web

docker stop web
docker rm web
docker rmi nginx
```

## Test

Open `http://localhost:8080`. The Nginx welcome page should appear while the container is running.

## Expected observations
- `docker images`: lists downloaded images.
- `docker ps`: lists running containers.
- `docker ps -a`: lists all containers, including stopped ones.
- `docker logs web`: displays container logs.
- `docker inspect web`: displays detailed configuration.
- `docker stats web`: displays CPU, memory, network and block-I/O usage.

**Result:** Image pulled, container started, inspected, stopped and removed.

**Viva:** Image = read-only template; container = running instance of an image; Dockerfile = instructions to build an image; `-d` = detached mode; `-p host:container` = port mapping.
