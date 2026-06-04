# CI/CD Pipeline Implementation Using Jenkins, Docker & AWS EC2

## Project Description

This project demonstrates the implementation of a complete CI/CD pipeline for deploying a Django web application using Jenkins, Docker, GitHub, and AWS EC2.

The objective of this project is to automate application deployment and showcase practical DevOps skills including source code management, containerization, continuous integration, continuous deployment, Linux administration, and cloud deployment.

---

# DevOps Technologies Used

## Version Control

* Git
* GitHub

## CI/CD

* Jenkins

## Containerization

* Docker

## Cloud Platform

* AWS EC2

## Operating System

* Amazon Linux

## Application Stack

* Python
* Django
* SQLite

---

# DevOps Skills Demonstrated

* Source Code Management using Git
* Repository Management using GitHub
* Linux Server Administration
* AWS EC2 Provisioning
* Docker Image Creation
* Docker Container Management
* Jenkins Installation and Configuration
* Jenkins Agent Configuration
* Continuous Integration (CI)
* Continuous Deployment (CD)
* Application Deployment Automation
* Process Monitoring and Troubleshooting

---

# Project Workflow

```text
Developer Pushes Code
          ↓
       GitHub
          ↓
       Jenkins
          ↓
     Build Process
          ↓
   Docker Image Build
          ↓
 Container Deployment
          ↓
      AWS EC2 Server
          ↓
 Live Application
```

---

# Step 1: Local Environment Setup

Clone the repository.

```bash
git clone https://github.com/surajyadav29/todo.git
```

Install Virtual Environment.

```bash
pip install virtualenv
```

Create Virtual Environment.

```bash
virtualenv -p python3.14.3 env
```

Activate Virtual Environment.

### Windows

```powershell
.\env\Scripts\Activate.ps1
```

Move to project directory.

```bash
cd todo
```

Generate requirements file.

```bash
pip freeze > requirements.txt
```

---

# Step 2: Launch AWS EC2 Instance

Create an EC2 instance using Amazon Linux.

Configure Security Group:

| Port | Purpose            |
| ---- | ------------------ |
| 22   | SSH Access         |
| 8000 | Django Application |
| 8080 | Jenkins Server     |

Connect to EC2 using SSH.

Create project directory.

```bash
mkdir todo
cd todo
```

---

# Step 3: Install Git and Clone Repository

Install Git.

```bash
sudo yum install git -y
```

Clone Repository.

```bash
sudo git clone https://github.com/surajyadav29/todo.git
```

Move to project directory.

```bash
cd todo
```

Verify Git Installation.

```bash
git --version
```

---

# Step 4: Install Python and Django

Install Python Package Manager.

```bash
sudo yum install python3-pip -y
```

Update Server Packages.

```bash
sudo yum update -y
```

Install Django.

```bash
pip install django
```

Verify Django.

```bash
python3 -m django --version
```

---

# Step 5: Run Django Application

Create database migrations.

```bash
python3.9 manage.py makemigrations
```

Apply migrations.

```bash
python3.9 manage.py migrate
```

Run application.

```bash
python3 manage.py runserver 0.0.0.0:8000
```

Run application in background.

```bash
nohup python3.9 manage.py runserver 0.0.0.0:8000 &
```

Application URL:

```text
http://<EC2-Public-IP>:8000
```

---

# Step 6: Linux Troubleshooting Commands

Check running process on port 8000.

```bash
lsof -i:8000
```

Kill process.

```bash
kill -9 PID
```

Restart application.

```bash
python3 manage.py runserver 0.0.0.0:8000
```

---

# Step 7: Install Docker

Install Docker.

```bash
sudo yum install docker -y
```

Start Docker Service.

```bash
sudo systemctl start docker
```

Enable Docker Service.

```bash
sudo systemctl enable docker
```

Verify Installation.

```bash
docker --version
```

---

# Step 8: Create Dockerfile

Create Dockerfile.

```bash
sudo vi Dockerfile
```

Dockerfile:

```dockerfile
FROM python:3.12

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

RUN python manage.py migrate

CMD ["python","manage.py","runserver","0.0.0.0:8000"]
```

---

# Step 9: Build Docker Image

Build Docker image.

```bash
sudo docker build . -t todo
```

Verify image.

```bash
sudo docker images
```

---

# Step 10: Deploy Docker Container

Run container.

```bash
sudo docker run -d -p 8000:8000 --name todo-app todo
```

Check running containers.

```bash
sudo docker ps
```

Application URL:

```text
http://<EC2-Public-IP>:8000
```

---

# Step 11: Install Jenkins Using Docker

Pull Jenkins Image.

```bash
sudo docker pull jenkins/jenkins:latest
```

Run Jenkins Container.

```bash
sudo docker run -d -p 8080:8080 docker.io/jenkins/jenkins:latest
```

Verify Jenkins Container.

```bash
sudo docker ps
```

Get Jenkins Initial Password.

```bash
sudo docker logs <container-id>
```

Access Jenkins.

```text
http://<EC2-Public-IP>:8080
```

Install Suggested Plugins and Create Admin User.

---

# Step 12: Configure Jenkins Agent

Create Jenkins Node/Agent.

Agent Configuration:

```text
Name : todo-agent

Remote Root Directory : <output of pwd>

Labels : todo
```

Provide project permissions.

```bash
cd ..
chmod 777 todo
cd todo
```

---

# Step 13: Create Jenkins Build Job

Configure Jenkins Job:

* Source Code Management → Git
* Repository URL → GitHub Repository
* Build Trigger → Build Now / GitHub Webhook
* Agent Label → todo

Build Commands:

```bash
sudo docker build . -t todo
```

Deploy Commands:

```bash
sudo docker run -d -p 8000:8000 todo
```

---

# Step 14: Application Update Process

Whenever new code is pushed:

1. Developer pushes code to GitHub.
2. Jenkins fetches latest source code.
3. Jenkins builds Docker image.
4. Existing container is stopped.
5. New container is deployed.
6. Updated application becomes available.

---

# Docker Maintenance Commands

List Containers.

```bash
sudo docker ps
```

Stop Container.

```bash
sudo docker stop <container-id>
```

Remove Container.

```bash
sudo docker rm <container-id>
```

View Logs.

```bash
sudo docker logs <container-id>
```

List Images.

```bash
sudo docker images
```

Remove Image.

```bash
sudo docker rmi <image-id>
```

---

# Learning Outcomes

This project helped in gaining hands-on experience with:

* Git and GitHub Workflow
* Linux Commands and Server Administration
* AWS EC2 Management
* Docker Containerization
* Jenkins Automation
* CI/CD Pipeline Implementation
* Application Deployment Automation
* Troubleshooting Deployment Issues
* Infrastructure Management

---

# Future Improvements

* Jenkins Pipeline as Code (Jenkinsfile)
* Docker Compose
* Nginx Reverse Proxy
* HTTPS/SSL Configuration
* Docker Hub Integration
* Kubernetes Deployment
* Terraform Infrastructure Automation
* SonarQube Code Quality Scans
* Prometheus Monitoring
* Grafana Dashboards

---

## Author

Suraj Yadav

DevOps Engineer | AWS | Docker | Jenkins | CI/CD
