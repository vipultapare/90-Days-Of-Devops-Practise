# Day 30 – Docker Images & Container Lifecycle

## 1. Docker Images

### Pull Images

```bash
docker pull nginx
docker pull ubuntu
docker pull alpine
```

### List Images

```bash
docker images
```

Observation:

* `ubuntu` image size is large (~70–80MB)
* `alpine` is very small (~5–7MB)
* Alpine is smaller because it is a minimal Linux distribution designed for containers.

**Screenshot:** docker images output

---

### Inspect an Image

```bash
docker inspect nginx
```

Information available:

* Image ID
* Layers
* Environment variables
* Default command
* Architecture
* Creation time

---

### Remove an Image

```bash
docker rmi ubuntu
```

---

## 2. Image Layers

### View Image History

```bash
docker image history nginx
```

Observation:

* Each line represents a layer
* Some layers show size
* Some show **0B** (metadata changes)

### What are Layers?

* Docker images are built in **layers**
* Each command in a Dockerfile creates a layer
* Layers are cached and reused
* This makes builds faster and saves storage

**Why Docker uses layers**

* Efficient storage
* Faster image builds
* Easy image sharing and updates

**Screenshot:** docker image history output

---

## 3. Container Lifecycle

### Create Container (without starting)

```bash
docker create --name test-container nginx
```

Check status:

```bash
docker ps -a
```

State: **Created**

---

### Start Container

```bash
docker start test-container
```

State: **Running**

---

### Pause Container

```bash
docker pause test-container
```

State: **Paused**

---

### Unpause Container

```bash
docker unpause test-container
```

---

### Stop Container

```bash
docker stop test-container
```

State: **Exited**

---

### Restart Container

```bash
docker restart test-container
```

---

### Kill Container

```bash
docker kill test-container
```

---

### Remove Container

```bash
docker rm test-container
```

Observation:

* Container states change between Created → Running → Paused → Exited → Removed

**Screenshot:** docker ps -a states

---

## 4. Working with Running Containers

### Run Nginx in Detached Mode

```bash
docker run -d -p 8080:80 --name nginx-demo nginx
```

---

### View Logs

```bash
docker logs nginx-demo
```

### Follow Logs (Real-time)

```bash
docker logs -f nginx-demo
```

---

### Exec into Container

```bash
docker exec -it nginx-demo bash
```

Explore filesystem:

```bash
ls /
exit
```

---

### Run Single Command Inside Container

```bash
docker exec nginx-demo ls /usr/share/nginx/html
```

---

### Inspect Container

```bash
docker inspect nginx-demo
```

Find:

* Container IP address
* Port mappings
* Network settings
* Mounts

**Screenshot:** docker inspect output

---

## 5. Cleanup

### Stop All Running Containers

```bash
docker stop $(docker ps -q)
```

---

### Remove All Stopped Containers

```bash
docker container prune
```

---

### Remove Unused Images

```bash
docker image prune -a
```

---

### Check Docker Disk Usage

```bash
docker system df
```

---

## Key Learnings

* Images are templates; containers are running instances
* Docker images use layered architecture for efficiency
* Containers go through multiple lifecycle states
* Logs, inspect, and exec are essential for troubleshooting
* Regular cleanup prevents disk space issues

---

## Screenshots to Attach

1. docker images output
2. docker image history nginx
3. docker ps -a lifecycle states
4. docker inspect nginx-demo

---

## Summary

Today I explored Docker image layers, container lifecycle, inspection, logging, and cleanup. Understanding image structure and container states is essential for managing containers in real DevOps environments.

