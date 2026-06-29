# DevBoard – Dockerized Three-Tier Application

## Overview

This repository demonstrates my **DevOps and containerization skills** by dockerizing an existing three-tier web application.

> **Disclaimer**
>
> The application source code was originally provided as part of a DevOps training program for learning purposes.
>
> **I am not the original developer of the Devboard application.**
>
> My contribution focuses on the DevOps and infrastructure side of the project, including:
>
> * Writing Dockerfiles
> * Containerizing the application
> * Creating Docker networks
> * Building and running Docker images
> * Multi-container deployment
> * (Upcoming) CI/CD implementation
> * (Upcoming) Kubernetes deployment
> * (Upcoming) Security best practices

---

# Project Architecture

* Frontend (React.js)
* Backend (Go)
* PostgreSQL Database

The application is deployed as a three-tier architecture using Docker containers connected through a custom Docker network.

---

# Technologies Used

* Docker
* Docker Networking
* Docker Images
* Docker Containers
* React.js
* Golang
* PostgreSQL

---

# Current Progress

* ✅ Dockerfiles created for frontend and backend
* ✅ PostgreSQL container configured
* ✅ Docker network configured
* ✅ Three-tier application deployed successfully using Docker
* 🔄 CI Pipeline (In Progress)
* 🔄 CD Pipeline (Planned)
* 🔄 Kubernetes Deployment (Planned)
* 🔄 Security Hardening (Planned)

---

# Build Docker Images

## Frontend

```bash
docker build -t devboard-frontend ./frontend
```

## Backend

```bash
docker build -t devboard-backend ./backend
```

---

# Create Docker Network

```bash
docker network create dev-net
```

---

# Run PostgreSQL

```bash
docker run -d \
--name postgres \
--network dev-net \
-e POSTGRES_DB=<database_name> \
-e POSTGRES_USER=<username> \
-e POSTGRES_PASSWORD=<password> \
-p 5432:5432 \
postgres:16-alpine
```

---

# Run Backend

```bash
docker run -d \
--name backend \
--network dev-net \
-p 8080:8080 \
devboard-backend
```

---

# Run Frontend

```bash
docker run -d \
--name frontend \
--network devboard-network \
-p 4173:4173 \
devboard-frontend
```

---

# Verify Running Containers

```bash
docker ps
```

---

# Verify Network

```bash
docker network inspect dev-net
```

---

# Stop Containers

```bash
docker stop <FRONTEND_CONTAINER_ID> <BACKEND_CONTAINER_ID> <DATABASE_CONTAINER_ID>
or
docker stop <FRONTEND_CONTAINER_NAME> <BACKEND_CONTAINER_NAME> <DATABASE_CONTAINER_NAME>
```

---

# Remove Containers

```bash
docker rm <FRONTEND_CONTAINER_ID> <BACKEND_CONTAINER_ID> <DATABASE_CONTAINER_ID>
or
docker stop <FRONTEND_CONTAINER_NAME> <BACKEND_CONTAINER_NAME> <DATABASE_CONTAINER_NAME>
```

---

# Remove Images

```bash
docker rmi <IMAGE_IDs>
```

---

# Learning Objectives

This repository is part of my DevOps learning journey, where I practice:

* Docker
* Containerization
* Infrastructure Automation
* CI/CD
* Kubernetes
* Cloud Deployment
* DevOps Best Practices

As I continue learning, this repository will evolve with additional DevOps implementations.
