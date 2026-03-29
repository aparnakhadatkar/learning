# 🐳 Dockerize Project — Step‑by‑Step Lab Guide (Beginner Friendly)

This guide helps you **Dockerize your first project** with **clear steps + meaning + where to perform**.

---

# 🎯 Lab Goal

You will:

* Create simple web app
* Create Dockerfile
* Build Docker image
* Run container
* Access application

---

# 🖥️ Where To Perform This Lab

Perform in:

✅ WSL Ubuntu Terminal (Recommended)
✅ Linux Machine
✅ Cloud VM

For Windows Users:

Open:

* Windows Terminal → Ubuntu
  OR
* Search "Ubuntu" in Windows

You should see:

```
username@DESKTOP:/home/user$
```

---

# Step 0 — Check Docker Installation

Run:

```bash
docker --version
```

Meaning:

* Checks Docker installation

Expected Output:

```
Docker version 24.x.x
```

---

# Step 1 — Create Project Folder

Run:

```bash
mkdir docker-lab
cd docker-lab
```

Meaning:

* mkdir → create folder
* cd → move into folder

Check location:

```bash
pwd
```

---

# Step 2 — Create HTML File

Run:

```bash
nano index.html
```

Paste:

```html
<html>
<head>
<title>Docker Lab</title>
</head>
<body>
<h1>Hello from Docker 🚀</h1>
<h2>My First Docker App</h2>
</body>
</html>
```

Save:

```
CTRL + X
Y
Enter
```

Verify:

```bash
ls
```

---

# Step 3 — Create Dockerfile

Run:

```bash
nano Dockerfile
```

Paste:

```dockerfile
FROM nginx

COPY . /usr/share/nginx/html
```

Meaning:

FROM nginx

* Use nginx base image

COPY . /usr/share/nginx/html

* Copy files to nginx web folder

Save:

```
CTRL + X
Y
Enter
```

Verify:

```bash
ls
```

Expected:

```
Dockerfile
index.html
```

---

# Step 4 — Build Docker Image

Run:

```bash
docker build -t docker-lab .
```

Meaning:

* docker build → build image
* -t docker-lab → image name
* . → current directory

Verify:

```bash
docker images
```

---

# Step 5 — Run Container

Run:

```bash
docker run -d -p 8080:80 docker-lab
```

Meaning:

| Command    | Meaning         |
| ---------- | --------------- |
| docker run | run container   |
| -d         | background mode |
| -p         | port mapping    |
| 8080       | local port      |
| 80         | container port  |

---

# Step 6 — Check Running Container

Run:

```bash
docker ps
```

Expected Output:

```
CONTAINER ID
IMAGE docker-lab
PORTS 8080:80
```

---

# Step 7 — Access Application

Open Browser:

```
http://localhost:8080
```

You should see:

```
Hello from Docker
```

🎉 Congratulations — You Dockerized your first project

---

# Step 8 — Stop Container

Run:

```bash
docker stop <container-id>
```

Example:

```bash
docker stop abc123
```

---

# Step 9 — Remove Container

Run:

```bash
docker rm <container-id>
```

---

# Step 10 — Remove Image

Run:

```bash
docker rmi docker-lab
```

---

# 📊 Docker Workflow

```
Create App
   ↓
Create Dockerfile
   ↓
Build Image
   ↓
Run Container
   ↓
Access Application
```

---

# 🧠 Important Docker Commands

Build Image

```bash
docker build -t app .
```

Run Container

```bash
docker run -p 8080:80 app
```

Check Containers

```bash
docker ps
```

Stop Container

```bash
docker stop id
```

Remove Container

```bash
docker rm id
```

---

# 🎯 What You Learned

✅ Dockerfile
✅ Docker Image
✅ Container
✅ Port Mapping
✅ Docker Workflow

---

# 🚀 Next Labs

Next Practice:

1. Dockerize Python App
2. Docker Compose Lab
3. Multi Container Lab
4. Kubernetes Deployment

---

# 🏆 Real‑World Use Case

Companies Dockerize:

* Backend API
* Frontend
* Database
* Microservices

Deploy To:

* Kubernetes
* AWS
* Azure
* GCP

---

# End of Lab

Happy Learning 🚀
