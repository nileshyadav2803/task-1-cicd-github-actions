````markdown
# 🚀 Task 1 — Node.js CI/CD Pipeline with GitHub Actions & Docker

[![Node.js](https://img.shields.io/badge/Node.js-20-339933?logo=node.js&logoColor=white)](https://nodejs.org/)
[![Docker](https://img.shields.io/badge/Docker-Containerized-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?logo=githubactions&logoColor=white)](https://github.com/features/actions)
[![Docker Hub](https://img.shields.io/badge/Docker%20Hub-Image%20Registry-2496ED?logo=docker&logoColor=white)](https://hub.docker.com/)

> A practical DevOps internship project demonstrating Node.js application development, Git version control, Docker containerization, and automated CI/CD using GitHub Actions.

---

## 📌 Project Overview

This project implements a basic **CI/CD pipeline for a Node.js application**.

The pipeline automatically:

- Checks out the source code
- Sets up Node.js
- Installs dependencies
- Validates the Node.js code
- Logs in to Docker Hub securely
- Builds a Docker image
- Pushes the image to Docker Hub

---

## 🔄 CI/CD Pipeline

```text
                 👨‍💻 Developer
                       │
                       │ git push
                       ▼
                ┌─────────────┐
                │   GitHub    │
                │    main     │
                └──────┬──────┘
                       │
                       ▼
             ┌───────────────────┐
             │  GitHub Actions   │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │  Checkout Code    │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │ Setup Node.js 20  │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │ Install Packages  │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │ Validate Code     │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │ Docker Hub Login  │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │ Docker Build      │
             └─────────┬─────────┘
                       │
             ┌─────────▼─────────┐
             │ Docker Hub Push   │
             └─────────┬─────────┘
                       │
                       ▼
                 🐳 Docker Hub
````

> **Note:** This project builds and pushes the Docker image to Docker Hub. AWS EC2 or production deployment is not implemented in this task.

---

## 🛠️ Tech Stack

| Technology     | Purpose                 |
| -------------- | ----------------------- |
| Node.js 20     | Application runtime     |
| JavaScript     | Application development |
| Git            | Version control         |
| GitHub         | Source code repository  |
| GitHub Actions | CI/CD automation        |
| Docker         | Containerization        |
| Docker Hub     | Docker image registry   |
| VS Code        | Development environment |

---

## 📂 Project Structure

```text
Task-1-CICD/
│
├── .github/
│   └── workflows/
│       └── main.yml
│
├── Dockerfile
├── package.json
├── server.js
└── README.md
```

---

## 💻 Application

The project contains a simple Node.js HTTP server.

When the application is running, it returns:

```text
Hello from Node.js CI/CD Pipeline!
```

### Run Locally

```bash
npm install
npm start
```

Open:

```text
http://localhost:3000
```

Stop the application with:

```text
Ctrl + C
```

---

## 🐳 Docker

### Build the Docker Image

```bash
docker build -t task-1-cicd .
```

### Run the Docker Container

```bash
docker run -p 3000:3000 task-1-cicd
```

Then open:

```text
http://localhost:3000
```

---

## ⚙️ GitHub Actions Workflow

The CI/CD workflow is located at:

```text
.github/workflows/main.yml
```

The workflow runs automatically when code is pushed to the `main` branch.

It can also be triggered manually using GitHub Actions.

### Workflow Stages

```text
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
Push Image to Docker Hub
```

---

## 🔐 GitHub Actions Secrets

Docker Hub credentials are stored securely using **GitHub Actions Secrets**.

Go to:

**Repository → Settings → Secrets and variables → Actions**

Add:

| Secret               | Value                            |
| -------------------- | -------------------------------- |
| `DOCKERHUB_USERNAME` | Docker Hub username              |
| `DOCKERHUB_TOKEN`    | Docker Hub Personal Access Token |

The workflow accesses them using:

```text
${{ secrets.DOCKERHUB_USERNAME }}
${{ secrets.DOCKERHUB_TOKEN }}
```

### 🔒 Security

The Docker Hub Personal Access Token is **not stored directly inside the workflow file**.

---

## 🧪 Code Validation

The pipeline uses:

```bash
node --check server.js
```

This checks the JavaScript syntax of `server.js`.

> This is a syntax validation step, not a complete automated test suite.

---

## 🐳 Docker Hub Image

The successful pipeline pushes the Docker image:

```text
nileshyadavny/task-1-cicd:latest
```

The `latest` tag represents the Docker image produced by the successful pipeline.

---

## ❌ Error Faced During Implementation

### Error

```text
Error: Username and password required
```

### Why Did It Happen?

GitHub Actions could not authenticate with Docker Hub because the required Docker Hub credentials had not been configured as GitHub Secrets.

### Fix

Added:

```text
DOCKERHUB_USERNAME
DOCKERHUB_TOKEN
```

under:

**GitHub Repository → Settings → Secrets and variables → Actions**

Then the workflow was run again.

### Result

```text
Docker Hub Login     ✅
Docker Image Build   ✅
Docker Image Push    ✅
```

---

## 📊 Final Result

```text
GitHub Push
     ↓
GitHub Actions
     ↓
Node.js Validation ✅
     ↓
Docker Build ✅
     ↓
Docker Hub Login ✅
     ↓
Docker Image Push ✅
```

The Docker image was successfully built and pushed to Docker Hub.

---

## 🧠 What I Learned

* Git repository and GitHub workflow
* Basic Node.js application setup
* Docker image creation
* Docker container execution
* GitHub Actions
* CI/CD pipeline automation
* GitHub Actions Secrets
* Docker Hub image publishing
* Troubleshooting CI/CD failures

---

## 📖 Key Concepts

<details>
<summary>🔹 What is CI?</summary>

**Continuous Integration (CI)** is the practice of automatically validating code changes when developers push code to a shared repository.

In this project, GitHub Actions installs dependencies and validates the Node.js source code.

</details>

<details>
<summary>🔹 What is CD?</summary>

**Continuous Delivery/Deployment (CD)** automates the steps performed after code validation.

In this project, the successful pipeline builds a Docker image and pushes it to Docker Hub.

</details>

<details>
<summary>🔹 Why Docker?</summary>

Docker packages an application and its runtime environment into a container image, helping the application run consistently across environments.

</details>

<details>
<summary>🔹 Why GitHub Secrets?</summary>

GitHub Secrets allow sensitive values such as Docker Hub tokens to be used by workflows without exposing them directly in the source code.

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

---

## 📚 Repository Workflow

```text
Write Code
    ↓
Test Locally
    ↓
Git Add
    ↓
Git Commit
    ↓
Git Push
    ↓
GitHub Actions
    ↓
Docker Build
    ↓
Docker Hub
```