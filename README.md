# Node-Dockerized-Project
# 🚀 Dockerized Node.js App with Jenkins CI/CD

A simple **Node.js Express** application, containerized using **Docker** and deployed via a **Jenkins pipeline** on AWS EC2. Demonstrates end-to-end CI/CD from code push to live Docker container.

---

## 🧰 Tech Stack

- **Node.js** (Express)
- **Docker** (Dockerfile for image creation)
- **Jenkins** (Pipeline for automation)
- **AWS EC2** (Deployment host)
- **GitHub** (Source code)

---

## ⚙️ Project Structure

Node-Dockerized-Project/
├── app.js
├── package.json
├── Dockerfile
├── .dockerignore
├── Jenkinsfile
└── screenshots/
├── docker_build.png
├── docker_run.png
└── jenkins_pipeline.png


---

## 📦 Quick Start

### 1. Build Docker Image Locally

```bash
docker build -t nodejs-app .

docker run -d --name nodejs-app -p 3000:3000 nodejs-app



🤖 Jenkins CI/CD Pipeline

pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/A-Bhagat22/Node-Dockerized-Project.git', branch: 'main'
      }
    }
    stage('Build Image') {
      steps {
        script { docker.build('nodejs-app') }
      }
    }
    stage('Deploy Container') {
      steps {
        sh 'docker rm -f nodejs-app || true'
        sh 'docker run -d --name nodejs-app -p 3000:3000 nodejs-app'
      }
    }
  }
}
Pipeline automatically builds and deploys the app on EC2 whenever code is pushed to GitHub.



