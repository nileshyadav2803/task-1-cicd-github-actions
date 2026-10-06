````markdown
# 🚀 Task 1 — Node.js CI/CD Pipeline with GitHub Actions & Docker

[![Node.js](https://img.shields.io/badge/Node.js-20-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![Docker Hub](https://img.shields.io/badge/Docker%20Hub-Image%20Registry-2496ED?logo=docker&logoColor=white)](https://hub.docker.com/)
[![Status](https://img.shields.io/badge/Status-Completed-success)](#-project-status)
[![Version](https://img.shields.io/badge/Version-v1.0.0-blue)](#-versioning)

> A practical DevOps internship project demonstrating **Node.js application development, Git version control, Docker containerization, GitHub Actions CI/CD automation, GitHub Secrets, and Docker Hub image publishing**.

---

## 📌 Table of Contents

- [🎯 Project Overview](#-project-overview)
- [🏗️ Architecture](#️-architecture)
- [🛠️ Tools Used](#️-tools-used)
- [📁 Project Structure](#-project-structure)
- [💻 Application](#-application)
- [🐳 Docker](#-docker)
- [🔄 CI/CD Workflow](#-cicd-workflow)
- [⚙️ GitHub Actions](#️-github-actions)
- [🔐 GitHub Secrets](#-github-secrets)
- [🐳 Docker Hub](#-docker-hub)
- [🧪 Validation](#-validation)
- [⚠️ Error Encountered & Fix](#️-error-encountered--fix)
- [🎓 What I Learned](#-what-i-learned)
- [🧠 Key Commands](#-key-commands)
- [🏷️ Versioning](#️-versioning)
- [🚀 Future Improvements](#-future-improvements)
- [✅ Project Status](#-project-status)
- [🏁 Conclusion](#-conclusion)

---

## 🎯 Project Overview

The objective of this project was to build a simple but practical **CI/CD pipeline for a Node.js application**.

The project demonstrates how a developer can:

- Create and run a Node.js application
- Test the application locally
- Containerize the application using Docker
- Manage source code using Git and GitHub
- Automate the CI/CD workflow using GitHub Actions
- Validate JavaScript syntax automatically
- Authenticate securely with Docker Hub using GitHub Secrets
- Build a Docker image automatically
- Push the Docker image to Docker Hub

### 🎯 Final Pipeline

```text
Developer
    │
    │ git push
    ▼
┌─────────────┐
│   GitHub    │
│    main     │
└──────┬──────┘
       │
       ▼
┌──────────────────┐
│  GitHub Actions  │
└────────┬─────────┘
         │
         ├── Checkout Code
         ├── Setup Node.js 20
         ├── Install Dependencies
         ├── Validate JavaScript
         ├── Login to Docker Hub
         ├── Build Docker Image
         └── Push Image
                  │
                  ▼
        ┌──────────────────┐
        │    Docker Hub    │
        │ task-1-cicd:     │
        │     latest       │
        └──────────────────┘
````

> **Project scope:** The implemented pipeline ends at Docker Hub image publishing. EC2 deployment or production/cloud deployment was **not** implemented in this task.

---

## 🏗️ Architecture

```text
                 ┌──────────────────┐
                 │    Developer     │
                 │  Node.js Source  │
                 └────────┬─────────┘
                          │
                       git push
                          │
                          ▼
                 ┌──────────────────┐
                 │      GitHub      │
                 │   main branch    │
                 └────────┬─────────┘
                          │
                    Workflow Trigger
                          │
                          ▼
                 ┌──────────────────┐
                 │ GitHub Actions   │
                 │      Runner      │
                 └────────┬─────────┘
                          │
             ┌────────────┼────────────┐
             │            │            │
             ▼            ▼            ▼
          Node.js       Docker       Secrets
         Validation      Build       Login
             │            │            │
             └────────────┼────────────┘
                          │
                          ▼
                 ┌──────────────────┐
                 │    Docker Hub    │
                 │ task-1-cicd:     │
                 │     latest       │
                 └──────────────────┘
```

---

## 🛠️ Tools Used

| Tool               | Purpose                       |
| ------------------ | ----------------------------- |
| **Node.js 20**     | Application runtime           |
| **JavaScript**     | Application source code       |
| **Git**            | Version control               |
| **GitHub**         | Remote source-code repository |
| **GitHub Actions** | CI/CD automation              |
| **Docker**         | Application containerization  |
| **Docker Hub**     | Docker image registry         |
| **VS Code**        | Development environment       |

---

## 📁 Project Structure

```text
Task-1-CICD/
│
├── 📂 .github/
│   └── 📂 workflows/
│       └── 📄 main.yml
│
├── 📄 server.js
├── 📄 package.json
├── 📄 Dockerfile
└── 📄 README.md
```

### File Purpose

| File / Folder                | Purpose                                    |
| ---------------------------- | ------------------------------------------ |
| `server.js`                  | Node.js HTTP application                   |
| `package.json`               | Project metadata and npm scripts           |
| `Dockerfile`                 | Instructions for building the Docker image |
| `.github/workflows/main.yml` | GitHub Actions CI/CD workflow              |
| `README.md`                  | Project documentation                      |

---

## 💻 Application

The application is a simple Node.js HTTP server.

When the application runs successfully, it returns:

```text
Hello from Node.js CI/CD Pipeline!
```

### Run Locally

Install dependencies:

```bash
npm install
```

Start the application:

```bash
npm start
```

Open:

```text
http://localhost:3000
```

### Expected Result

```text
Hello from Node.js CI/CD Pipeline!
```

Stop the application with:

```text
Ctrl + C
```

---

## 🐳 Docker

The Node.js application is containerized using Docker.

### Build Image

```bash
docker build -t task-1-cicd .
```

### Run Container

```bash
docker run -p 3000:3000 task-1-cicd
```

Open:

```text
http://localhost:3000
```

The application should return:

```text
Hello from Node.js CI/CD Pipeline!
```

---

## 🔄 CI/CD Workflow

The complete workflow is:

```text
Code Change
     │
     ▼
git add .
     │
     ▼
git commit
     │
     ▼
git push origin main
     │
     ▼
GitHub Actions Triggered
     │
     ├── Checkout Code
     │
     ├── Setup Node.js 20
     │
     ├── npm install
     │
     ├── Validate server.js
     │
     ├── Login to Docker Hub
     │
     ├── Build Docker Image
     │
     └── Push Image to Docker Hub
```

### Workflow in Simple Terms

1. Developer pushes code to GitHub.
2. GitHub Actions automatically starts.
3. Repository code is checked out.
4. Node.js 20 is configured.
5. Dependencies are installed.
6. `server.js` syntax is validated.
7. GitHub Actions logs in to Docker Hub using secrets.
8. Docker image is built.
9. Image is pushed to Docker Hub.
10. Successful pipeline completes the CI/CD process.

---

## ⚙️ GitHub Actions

The workflow is stored at:

```text
.github/workflows/main.yml
```

The workflow runs when code is pushed to:

```text
main
```

It can also be manually triggered using:

```text
workflow_dispatch
```

### Main Pipeline Stages

| Stage                | Purpose                                   |
| -------------------- | ----------------------------------------- |
| Checkout Code        | Downloads repository code into the runner |
| Setup Node.js        | Provides Node.js 20 environment           |
| Install Dependencies | Installs npm dependencies                 |
| Validate Code        | Checks JavaScript syntax                  |
| Docker Login         | Authenticates with Docker Hub             |
| Docker Build         | Creates the container image               |
| Docker Push          | Publishes image to Docker Hub             |

---

## 🔐 GitHub Secrets

Docker Hub credentials were not hard-coded into the workflow.

The repository uses GitHub Actions Secrets:

```text
DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
```

### Configure Secrets

Go to:

```text
GitHub Repository
      ↓
Settings
      ↓
Secrets and variables
      ↓
Actions
```

Add:

| Secret               | Purpose                          |
| -------------------- | -------------------------------- |
| `DOCKERHUB_USERNAME` | Docker Hub username              |
| `DOCKERHUB_TOKEN`    | Docker Hub Personal Access Token |

The workflow accesses them securely through GitHub's secrets mechanism.

```text
${{ secrets.DOCKERHUB_USERNAME }}
${{ secrets.DOCKERHUB_TOKEN }}
```

> 🔒 **Security:** Never commit or display the Docker Hub Personal Access Token in source code.

---

## 🐳 Docker Hub

The pipeline publishes the Docker image as:

```text
nileshyadavny/task-1-cicd:latest
```

The `latest` tag represents the image produced by the successful pipeline.

### Result

```text
GitHub
   ↓
GitHub Actions
   ↓
Docker Build
   ↓
Docker Hub
   ↓
nileshyadavny/task-1-cicd:latest
```

---

## 🧪 Validation

The pipeline performs JavaScript syntax validation using:

```bash
node --check server.js
```

### Important

This command checks whether the JavaScript syntax is valid.

It is **not a complete automated application test suite**.

The application was also manually tested locally using:

```bash
npm start
```

and verified through:

```text
http://localhost:3000
```

---

## ⚠️ Error Encountered & Fix

### ❌ Docker Hub Login Error

During the first GitHub Actions run, the workflow failed at the Docker Hub login step.

The error was:

```text
Error: Username and password required
```

### 🔍 Why Did It Happen?

The workflow expected Docker Hub credentials from GitHub Actions Secrets, but the required secrets had not been configured yet.

### ✅ Resolution

Added:

```text
DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
```

to:

```text
Repository
→ Settings
→ Secrets and variables
→ Actions
```

Then the workflow was rerun.

### ✅ Final Result

The workflow completed successfully and the Docker image was pushed to Docker Hub.

### 🧠 Key Takeaway

> When a CI/CD workflow uses `${{ secrets.SOMETHING }}`, that secret must exist in the repository's GitHub Actions Secrets before the workflow can authenticate successfully.


## 🎓 What I Learned

Through this project, I learned and practiced:

* Node.js application basics
* Git repository workflow
* GitHub repository management
* Dockerfile creation
* Docker image building
* Docker container execution
* GitHub Actions
* CI/CD pipeline structure
* GitHub Actions Secrets
* Docker Hub authentication
* Docker image publishing
* CI/CD troubleshooting
* Difference between CI validation and deployment

---

## 🧠 Key Commands

### Node.js

```bash
npm install
npm start
node --check server.js
```

### Git

```bash
git init
git add .
git commit -m "Add Node.js CI/CD pipeline"
git remote add origin <repository-url>
git push -u origin main
```

### Docker

```bash
docker build -t task-1-cicd .
docker run -p 3000:3000 task-1-cicd
```

---

## 🏷️ Versioning

The completed version of this project is identified as:

```text
v1.0.0
```

Version tags provide a fixed reference point for a completed project version.

---

## 🚀 Future Improvements

The current implementation ends at Docker Hub image publishing.

Possible future improvements:

* ☁️ Deploy the Docker image to AWS EC2
* 🧪 Add a complete automated test suite
* 🏷️ Use version-based Docker image tags
* 🔄 Add an automated deployment stage
* 📊 Add application monitoring
* 🔙 Add deployment rollback strategy
* 🔐 Improve container and secret security

---

## 📊 Project Status

| Requirement               | Status            |
| ------------------------- | ----------------- |
| Node.js application       | ✅ Complete        |
| Local application testing | ✅ Complete        |
| Dockerfile                | ✅ Complete        |
| Docker image build        | ✅ Complete        |
| Git repository            | ✅ Complete        |
| GitHub repository         | ✅ Complete        |
| GitHub Actions workflow   | ✅ Complete        |
| Node.js validation        | ✅ Complete        |
| Docker Hub authentication | ✅ Complete        |
| GitHub Secrets            | ✅ Complete        |
| Docker Hub image push     | ✅ Complete        |
| CI/CD verification        | ✅ Complete        |
| Cloud/EC2 deployment      | ⏳ Not implemented |

---

## 🏁 Conclusion

This project demonstrates a practical **Node.js CI/CD workflow using GitHub Actions and Docker**.

The application is automatically validated, containerized, and published to Docker Hub whenever changes are pushed to the `main` branch.

The project provided hands-on experience with the core DevOps flow:

```text
Code
  ↓
Git
  ↓
GitHub
  ↓
GitHub Actions
  ↓
Validation
  ↓
Docker Build
  ↓
Docker Hub
```

### 🚀 Final Status

Completed Node.js CI/CD Pipeline Project**

