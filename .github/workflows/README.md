# Node.js CI/CD Pipeline

## Project Overview
This project demonstrates CI/CD automation using GitHub Actions.

## Technologies Used
- Node.js
- Git and GitHub
- GitHub Actions
- Docker
- Docker Hub

## Application
A simple Node.js web application running on port 3000.

## CI/CD Workflow
1. Trigger the workflow when code is pushed to the main branch.
2. Install Node.js dependencies.
3. Validate the Node.js code.
4. Log in to Docker Hub using GitHub Secrets.
5. Build and push the Docker image to Docker Hub.

## Learning Objective
To understand automated code validation, Docker image building, and image publishing using GitHub Actions.