# Day 29 – Docker Basics

## 1. What is Docker?

### What is a Container?

A container is a lightweight, portable package that includes:

* Application code
* Dependencies
* Libraries
* Runtime

Containers ensure the application runs the same in **development, testing, and production**.

**Why containers?**

* Consistent environment
* Fast startup
* Lightweight compared to virtual machines
* Easy deployment and scaling

---

## 2. Containers vs Virtual Machines

| Feature        | Containers           | Virtual Machines       |
| -------------- | -------------------- | ---------------------- |
| Size           | Lightweight          | Heavy                  |
| Startup Time   | Seconds              | Minutes                |
| OS             | Share host OS kernel | Each VM has full OS    |
| Performance    | Faster               | Slower due to overhead |
| Resource Usage | Low                  | High                   |

**Summary:** Containers are efficient and ideal for modern DevOps workflows.

---

## 3. Docker Architecture

Docker consists of:

* **Docker Client** – Command line tool (`docker`)
* **Docker Daemon** – Background service that manages containers
* **Images** – Read-only templates used to create containers
* **Containers** – Running instances of images
* **Docker Registry** – Stores images (Docker Hub)

### Architecture Flow (in simple words)

User → Docker CLI → Docker Daemon → Pull Image from Docker Hub → Run Container

---

## 4. Docker Installation & Verification

### Check Docker version

```id="v1o3r0"
docker --version
```

### Run hello-world container

```id="q7chdx"
docker run hello-world
```

Observation:

* Docker pulled the image from Docker Hub
* Created and ran a container successfully

**Screenshot:** (Add hello-world output here)

---

## 5. Running Real Containers

### Run Nginx container

```id="g4ld4k"
docker run -d -p 8080:80 --name my-nginx nginx
```

Access in browser:

```
http://<your-server-ip>:8080
```

Observation:

* Nginx welcome page displayed

**Screenshot:** (Add browser screenshot)

---

### Run Ubuntu in interactive mode

```id="8n5i3h"
docker run -it ubuntu bash
```

Inside container:

```id="q3s9we"
ls
apt update
exit
```

Observation:

* Container works like a mini Linux system

---

## 6. Container Management Commands

### List running containers

```id="y4s4po"
docker ps
```

### List all containers

```id="0fnyo5"
docker ps -a
```

### Stop a container

```id="e8uv5o"
docker stop my-nginx
```

### Remove a container

```id="c3g7yd"
docker rm my-nginx
```

---

## 7. Exploring Docker Features

### Run container in detached mode

```id="z2m7qa"
docker run -d nginx
```

Detached mode runs the container in the background.

---

### Run with custom name and port mapping

```id="v8y9ok"
docker run -d -p 8081:80 --name web-server nginx
```

---

### Check container logs

```id="t1o6hi"
docker logs web-server
```

---

### Execute command inside running container

```id="g5p2kt"
docker exec -it web-server bash
```

Observation:

* Able to access container shell and run commands

---

## 8. Key Learnings

* Docker containers are lightweight and portable
* Images are used to create containers
* Port mapping allows external access
* Detached mode runs containers in background
* Logs and exec help in troubleshooting

Docker is the foundation for CI/CD, Kubernetes, and modern cloud deployments.

---

## Screenshots to Attach

1. hello-world container output
2. Nginx running in browser
3. `docker ps` output

---

## Summary

Today I installed Docker, ran my first containers, explored container management, and understood Docker architecture. This is the first step toward containerized deployments in DevOps.

