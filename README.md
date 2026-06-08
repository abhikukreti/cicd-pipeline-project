# CI/CD Pipeline Project

End-to-end CI/CD pipeline using Git, Jenkins, Docker, and Kubernetes.

## Tech Stack
- GitHub (Version Control)
- Jenkins (CI/CD)
- Docker + Docker Hub (Containerization)
- Kubernetes/Minikube (Orchestration)
- Node.js + Express (Application)

## Pipeline Flow
Git Push → Jenkins Trigger → Test → Docker Build → Docker Push → K8s Deploy

## App Endpoints
- GET / → CI/CD Pipeline App Running
- GET /health → {"status":"healthy"}

## Setup
See docs/setup-guide.md
