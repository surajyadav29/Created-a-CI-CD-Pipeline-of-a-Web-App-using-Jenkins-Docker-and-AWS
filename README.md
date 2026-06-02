# CI/CD Pipeline for Django Todo Application using Jenkins, Docker & AWS

## Project Overview

This project demonstrates the implementation of an end-to-end CI/CD pipeline for a Django Todo Application using Jenkins, Docker, GitHub, and AWS EC2.

The pipeline automates the entire software delivery lifecycle, including source code integration, Docker image creation, container deployment, and application updates on AWS infrastructure.

The goal of this project is to showcase DevOps practices such as Continuous Integration (CI), Continuous Deployment (CD), containerization, and cloud deployment.

---

## Application

**django-todo** is a simple Todo Application built using Django that allows users to create and manage tasks efficiently.

### Features

* Add Tasks
* Update Tasks
* Delete Tasks
* Mark Tasks as Completed
* Django Admin Panel
* Responsive UI

---

## Architecture Diagram

```text
Developer
    |
    v
 GitHub Repository
    |
    v
 Jenkins Pipeline
    |
    v
 Docker Build
    |
    v
 Docker Hub
    |
    v
 AWS EC2 Instance
    |
    v
 Running Django Todo Application
```

---

## Tech Stack

### Application

* Python
* Django
* SQLite

### DevOps

* Git & GitHub
* Jenkins
* Docker
* Docker Hub
* AWS EC2
* Linux (Ubuntu)
* Nginx

---

## CI/CD Pipeline Workflow

### Step 1: Source Code Push

Developer pushes code to GitHub repository.

### Step 2: Jenkins Trigger

GitHub Webhook triggers Jenkins Pipeline automatically.

### Step 3: Build Stage

Jenkins pulls the latest source code and prepares the build.

### Step 4: Docker Image Creation

Docker image is built using Dockerfile.

```bash
docker build -t django-todo .
```

### Step 5: Push Image to Docker Hub

```bash
docker push username/django-todo:latest
```

### Step 6: Deployment on AWS EC2

AWS EC2 instance pulls the latest image and deploys the updated application.

```bash
docker pull username/django-todo:latest

docker stop django-todo

docker rm django-todo

docker run -d -p 8000:8000 --name django-todo username/django-todo:latest
```

### Pipeline Flow

```text
Developer
   ↓
GitHub
   ↓
Jenkins
   ↓
Docker Build
   ↓
Docker Hub
   ↓
AWS EC2 Deployment
   ↓
Live Django Todo App
```

---

## AWS Services Used

### AWS EC2

Used to host:

* Jenkins Server
* Dockerized Django Application

### Security Groups

Configured Ports:

* 22 (SSH)
* 80 (HTTP)
* 443 (HTTPS)
* 8080 (Jenkins)

---

## Project Screenshot

![todo App](https://raw.githubusercontent.com/shreys7/django-todo/develop/staticfiles/todoApp.png)

---

## Project Structure

```text
django-todo/
│
├── todoApp/
├── staticfiles/
├── templates/
├── Dockerfile
├── Jenkinsfile
├── manage.py
├── requirements.txt
├── README.md
│
├── screenshots/
│   ├── jenkins-success.png
│   ├── docker-build.png
│   ├── aws-ec2.png
│   └── deployed-app.png
│
└── scripts/
    └── deploy.sh
```

---

# Local Setup

## Clone Repository

```bash
git clone https://github.com/shreys7/django-todo.git
cd django-todo
```

---

## Install Dependencies

Make sure Python and Django are installed.

```bash
pip install -r requirements.txt
```

If Django is not installed, visit:

https://www.djangoproject.com/download/

---

## Run Migrations

```bash
python manage.py makemigrations
```

```bash
python manage.py migrate
```

---

## Create Admin User

```bash
python manage.py createsuperuser
```

Provide:

* Username
* Email
* Password

---

## Run Development Server

```bash
python manage.py runserver
```

Open:

```text
http://127.0.0.1:8000/todos
```

---

# Docker Setup

Build Docker Image

```bash
docker build -t django-todo .
```

Run Container

```bash
docker run -d -p 8000:8000 django-todo
```

Application URL

```text
http://localhost:8000/todos
```

---

# Jenkins Pipeline

The Jenkins pipeline automates:

* Source Code Checkout
* Build Process
* Docker Image Creation
* Docker Hub Push
* AWS EC2 Deployment

Example Stages:

```groovy
Pipeline
 ├── Checkout
 ├── Build
 ├── Test
 ├── Docker Build
 ├── Docker Push
 └── Deploy to AWS EC2
```

---

# Screenshots

Add screenshots to showcase successful implementation.

## Jenkins Pipeline Success

```text
screenshots/jenkins-success.png
```

## Docker Build

```text
screenshots/docker-build.png
```

## Docker Hub Repository

```text
screenshots/dockerhub-image.png
```

## AWS EC2 Deployment

```text
screenshots/aws-ec2.png
```

## Live Application

```text
screenshots/deployed-app.png
```

---

# Results & Benefits

### Achievements

* Automated end-to-end deployment process
* Reduced manual deployment effort
* Faster software delivery
* Improved deployment consistency
* Dockerized application deployment
* Cloud hosting on AWS

### DevOps Skills Demonstrated

* Continuous Integration (CI)
* Continuous Deployment (CD)
* Jenkins Pipeline Development
* Docker Containerization
* AWS EC2 Deployment
* Linux Administration
* Git Version Control

---

# Future Enhancements

* Kubernetes Deployment
* Terraform Infrastructure as Code
* SonarQube Code Analysis
* Prometheus Monitoring
* Grafana Dashboard
* Blue-Green Deployment Strategy
* Automated Rollback Mechanism
