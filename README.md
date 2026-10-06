# 🚀 Task 1 — Node.js CI/CD Pipeline with GitHub Actions & Docker

> A practical DevOps internship project demonstrating Node.js application development, Git version control, Docker containerization, GitHub Actions CI/CD, Docker Hub integration, secure GitHub Secrets, and pipeline troubleshooting.

---

## 📌 Table of Contents

* 🎯 Project Overview
* 🛠️ Tools Used
* 📁 Project Structure
* 🔄 CI/CD Workflow
* ⚙️ GitHub Actions Pipeline
* 🐳 Docker Configuration
* 🔐 GitHub Secrets
* 🧪 Application Testing
* ❌ Error Encountered & Fix
* 📦 Docker Hub
* 📚 Documentation
* 🎓 What I Learned
* 🧠 Key Concepts
* 📸 Evidence
* 🚀 Future Improvements
* ✅ Project Status
* 🏁 Conclusion

---

## 🎯 Project Overview

The objective of this project was to build a basic **CI/CD pipeline for a Node.js application** using GitHub Actions and Docker.

The project demonstrates how a developer can:

* Create a Node.js application
* Manage source code using Git and GitHub
* Containerize the application using Docker
* Automate validation using GitHub Actions
* Build a Docker image automatically
* Authenticate securely with Docker Hub
* Push the Docker image to Docker Hub
* Troubleshoot a failed CI/CD workflow

---

## 🛠️ Tools Used

| Tool           | Purpose                      |
| -------------- | ---------------------------- |
| Node.js 20     | Application runtime          |
| JavaScript     | Application development      |
| Git            | Version control              |
| GitHub         | Remote repository            |
| GitHub Actions | CI/CD automation             |
| Docker         | Application containerization |
| Docker Hub     | Docker image registry        |
| VS Code        | Development environment      |

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

| File / Folder                | Purpose                                |
| ---------------------------- | -------------------------------------- |
| `server.js`                  | Node.js HTTP application               |
| `package.json`               | Project metadata and npm scripts       |
| `Dockerfile`                 | Instructions to build the Docker image |
| `.github/workflows/main.yml` | GitHub Actions CI/CD workflow          |
| `README.md`                  | Project documentation                  |

---

## 🔄 CI/CD Workflow

The project follows this workflow:

```text
Local Development
       ↓
Node.js Application
       ↓
Git Add & Commit
       ↓
Git Push
       ↓
GitHub main Branch
       ↓
GitHub Actions
       ↓
Checkout Code
       ↓
Setup Node.js 20
       ↓
Install Dependencies
       ↓
Validate server.js
       ↓
Login to Docker Hub
       ↓
Build Docker Image
       ↓
Push Docker Image
       ↓
Docker Hub
```

### Workflow in Simple Terms

1. Created the Node.js application.
2. Tested the application locally.
3. Created the Dockerfile.
4. Initialized the Git repository.
5. Created the initial commit.
6. Connected the local repository to GitHub.
7. Pushed the project to the `main` branch.
8. Created the GitHub Actions workflow.
9. Configured Docker Hub credentials using GitHub Secrets.
10. GitHub Actions automatically installed dependencies.
11. The workflow validated the Node.js source code.
12. The workflow logged in to Docker Hub.
13. The Docker image was built.
14. The Docker image was pushed to Docker Hub.
15. The successful image was verified on Docker Hub.

---

## ⚙️ GitHub Actions Pipeline

The workflow file is:

```text
.github/workflows/main.yml
```

### Pipeline Stages

```text
Checkout Code
      ↓
Setup Node.js 20
      ↓
Install Dependencies
      ↓
Validate Node.js Code
      ↓
Login to Docker Hub
      ↓
Build Docker Image
      ↓
Push Docker Image
```

The workflow is triggered when code is pushed to the `main` branch.

It can also be manually triggered using GitHub Actions.

---

## 🐳 Docker Configuration

The application is containerized using Docker.

### Docker Image

The image is built using:

```bash
docker build -t task-1-cicd .
```

### Run Locally

```bash
docker run -p 3000:3000 task-1-cicd
```

The application can then be accessed at:

```text
http://localhost:3000
```

---

## 💻 Node.js Application

The project contains a simple Node.js HTTP server.

When the application runs successfully, it displays:

```text
Hello from Node.js CI/CD Pipeline!
```

### Run Without Docker

```bash
npm install
npm start
```

Open:

```text
http://localhost:3000
```

The server can be stopped using:

```text
Ctrl + C
```

---

## 🔐 GitHub Secrets

Docker Hub authentication is handled using **GitHub Actions Secrets**.

The following secrets were configured:

| Secret               | Purpose                          |
| -------------------- | -------------------------------- |
| `DOCKERHUB_USERNAME` | Docker Hub username              |
| `DOCKERHUB_TOKEN`    | Docker Hub Personal Access Token |

Secrets were configured from:

**GitHub Repository → Settings → Secrets and variables → Actions**

The workflow accesses the credentials using:

```text
${{ secrets.DOCKERHUB_USERNAME }}
${{ secrets.DOCKERHUB_TOKEN }}
```

### 🔒 Security

The Docker Hub Personal Access Token is not stored directly inside the workflow file.

---

## 🧪 Application Validation

The GitHub Actions workflow validates the JavaScript syntax using:

```bash
node --check server.js
```

This confirms that the JavaScript file has valid syntax.

> This is a syntax validation step and not a complete automated application test suite.

---

## ❌ Error Encountered During Implementation

### Docker Hub Login Error

During the first GitHub Actions run, the Docker Hub login step failed with:

```text
Error: Username and password required
```

### Why Did It Happen?

The workflow expected Docker Hub credentials from GitHub Secrets, but the required secrets had not been configured yet.

### Resolution

Configured:

```text
DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
```

under:

**GitHub Repository → Settings → Secrets and variables → Actions**

After configuring the secrets, the workflow was run again.

### Result

```text
Docker Hub Login     ✅
Docker Image Build   ✅
Docker Image Push    ✅
```

The complete GitHub Actions workflow then finished successfully.

---

## 📦 Docker Hub

The Docker image was pushed to Docker Hub using:

```text
nileshyadavny/task-1-cicd:latest
```

The `latest` tag represents the Docker image produced by the successful CI/CD pipeline.

---

## 📚 Documentation

The project documentation covers:

* Node.js application setup
* Local application testing
* Docker configuration
* Git repository setup
* GitHub repository setup
* GitHub Actions workflow
* Docker Hub authentication
* GitHub Secrets
* CI/CD workflow
* Error encountered during implementation
* Error resolution
* Final verification

---

## 🎓 What I Learned

Through this project, I learned and practiced:

* Basic Node.js application setup
* Git repository management
* GitHub repository workflow
* Docker image creation
* Docker container execution
* GitHub Actions
* CI/CD pipeline automation
* GitHub Actions Secrets
* Docker Hub authentication
* Docker image publishing
* CI/CD troubleshooting
* Basic DevOps workflow

---

## 🧠 Key Concepts

<details>
<summary>Click to view CI/CD concepts</summary>

### Continuous Integration

Continuous Integration automatically validates code changes when developers push code to a shared repository.

In this project, GitHub Actions installs dependencies and validates the Node.js source code.

### Continuous Delivery

Continuous Delivery automates the steps performed after code validation.

In this project, the pipeline builds a Docker image and pushes it to Docker Hub.

### Docker

Docker packages the application and its runtime environment into a container image.

### GitHub Actions

GitHub Actions automates the CI/CD workflow whenever changes are pushed to the repository.

### GitHub Secrets

GitHub Secrets securely store sensitive values such as Docker Hub credentials without putting them directly into the workflow file.

</details>

---

## 🚀 Future Improvements

Possible improvements for the next version:

* Deploy the Docker image to AWS EC2
* Add automated application tests
* Add version-based Docker image tags
* Add an automated deployment stage
* Add monitoring
* Add rollback strategy

> These features are not part of the current implementation.

---

## 📊 Final Pipeline Result

```text
GitHub Push
     ↓
GitHub Actions
     ↓
Checkout Code              ✅
     ↓
Setup Node.js              ✅
     ↓
Install Dependencies       ✅
     ↓
Validate Code              ✅
     ↓
Docker Hub Login           ✅
     ↓
Docker Image Build         ✅
     ↓
Docker Image Push          ✅
     ↓
Docker Hub                 ✅
```

---

## 🏷️ Project Scope

### Implemented

* Node.js application
* Git repository
* GitHub repository
* Dockerfile
* Docker image
* GitHub Actions CI/CD
* GitHub Secrets
* Docker Hub authentication
* Docker Hub image push
* CI/CD troubleshooting
* Project documentation

### Not Implemented

* AWS EC2 deployment
* Production deployment
* Cloud hosting
* Automated production release
* Monitoring

---

## ✅ Project Status

| Requirement               | Status               |
| ------------------------- | -------------------- |
| Node.js application       | ✅ Complete           |
| Local application testing | ✅ Complete           |
| Dockerfile                | ✅ Complete           |
| Docker image build        | ✅ Complete           |
| Git repository            | ✅ Complete           |
| GitHub repository         | ✅ Complete           |
| GitHub Actions workflow   | ✅ Complete           |
| Node.js validation        | ✅ Complete           |
| Docker Hub authentication | ✅ Complete           |
| GitHub Secrets            | ✅ Complete           |
| Docker Hub image push     | ✅ Complete           |
| CI/CD troubleshooting     | ✅ Complete           |
| README documentation      | ✅ Complete           |
| AWS deployment            | ⏳ Future Improvement |

---

## 🏁 Conclusion

This project demonstrates a practical **Node.js CI/CD workflow using GitHub Actions and Docker**.

The project successfully automates code validation, Docker image building, and Docker Hub image publishing.

It provides a foundation for extending the pipeline later with **AWS deployment, automated testing, monitoring, and production delivery**.

---

## 🚀 Final Result

**Node.js Application → GitHub → GitHub Actions → Docker → Docker Hub**

### Docker Image

```text
nileshyadavny/task-1-cicd:latest
```

---
