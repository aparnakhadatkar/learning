# Exercise 1: Multi‑Stage Docker Build – Docker Tutorial for Beginners (CKA)

### Estimated Duration: 30 Minutes

---

# Overview

This exercise introduces **Multi‑Stage Docker Builds**, an advanced Docker feature used to create **optimized, lightweight, and production‑ready container images**. Multi‑stage builds allow developers and DevOps engineers to separate build environments from runtime environments, resulting in **smaller images, improved security, and faster deployments**.

By the end of this exercise, you will understand how to build applications using multiple stages and deploy efficient containers suitable for **Kubernetes and production environments**.

---

# Objectives

You will be able to complete the following tasks:

* Task 1: Understand Multi‑Stage Docker Build Concept
* Task 2: Create Multi‑Stage Dockerfile
* Task 3: Build Multi‑Stage Docker Image
* Task 4: Run Multi‑Stage Container

---

# Task 1: Understanding Multi‑Stage Docker Build

In this task, you will learn the concept of **Multi‑Stage Docker Builds** and why they are used in real‑world DevOps environments.

## What is Multi‑Stage Docker Build?

Multi‑stage build allows you to use **multiple FROM statements** in one Dockerfile. Each stage performs a specific task such as:

* Build Application
* Install Dependencies
* Compile Code
* Copy Required Files
* Create Production Image

This helps in **removing unnecessary dependencies** from the final image.

---

## Why Multi‑Stage Build is Important

Traditional Docker Image Issues:

* Large Image Size
* Security Risks
* Slow Deployment
* Unnecessary Files Included

Multi‑Stage Build Benefits:

* Smaller Image Size
* Faster Deployment
* Improved Security
* Production Ready Images

---

# Task 2: Create Multi‑Stage Dockerfile

In this task, you will create a **Multi‑Stage Dockerfile**.

## Step 1: Create Project Folder

Open Terminal and Run:

```bash
mkdir multi-stage-docker
cd multi-stage-docker
```

---

## Step 2: Create Dockerfile

Run:

```bash
nano Dockerfile
```

Paste the following:

```dockerfile
# Stage 1 - Builder Stage
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build


# Stage 2 - Production Stage
FROM nginx:alpine

COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

Save File:

```
CTRL + X
Y
Enter
```

---

# Explanation of Dockerfile

## Stage 1 — Builder Stage

```
FROM node:18 AS builder
```

This creates a **builder stage** using Node.js image.

```
RUN npm install
```

Installs dependencies.

```
RUN npm run build
```

Builds application.

---

## Stage 2 — Production Stage

```
FROM nginx:alpine
```

Uses lightweight nginx image.

```
COPY --from=builder
```

Copies only required files from builder stage.

---

# Task 3: Build Multi‑Stage Docker Image

Run:

```bash
docker build -t multi-stage-app .
```

This builds optimized Docker image.

Verify Image:

```bash
docker images
```

---

# Task 4: Run Multi‑Stage Container

Run:

```bash
docker run -d -p 8080:80 multi-stage-app
```

Verify Container:

```bash
docker ps
```

---

# Access Application

Open Browser:

```
http://localhost:8080
```

You should see application running.

---

# Real‑World Use Cases

Multi‑Stage builds are used for:

* React Applications
* Node Applications
* Java Applications
* Python Applications
* Microservices

---

# Best Practices

* Use lightweight base images
* Remove unnecessary dependencies
* Use multi‑stage builds for production
* Keep images small

---

# Summary

In this exercise, you learned about **Multi‑Stage Docker Builds** and how they help create optimized container images. You created a Dockerfile with multiple stages, built the Docker image, and deployed the container. This approach improves performance, security, and deployment efficiency, making it ideal for **Kubernetes and production environments**.

---

# You have successfully completed this Exercise!

🚀 Next Exercise:

* Docker Compose Lab
* Kubernetes Deployment
* Push Image to DockerHub

---
