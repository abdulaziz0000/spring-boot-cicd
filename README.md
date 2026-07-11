# Spring Boot CI/CD Pipeline with GitHub Actions, Docker & AWS EC2

## Project Overview

This project demonstrates a complete CI/CD (Continuous Integration and Continuous Deployment) pipeline for a Spring Boot application using:

- Java 17
- Spring Boot
- Docker
- GitHub Actions
- Docker Hub
- AWS EC2

The pipeline automatically builds, packages, pushes, and deploys the application whenever code is pushed to the `main` branch.

---

## CI/CD Workflow

The pipeline performs the following steps automatically:

1. Checkout the latest source code from GitHub.
2. Build the Spring Boot application using Maven.
3. Build a Docker image.
4. Push the Docker image to Docker Hub.
5. Connect to an AWS EC2 instance via SSH.
6. Stop the existing Docker container (if running).
7. Remove the old container.
8. Pull the latest Docker image from Docker Hub.
9. Start a new Docker container on the EC2 instance.

---

## Technologies Used

- Java 17
- Spring Boot
- Maven
- Docker
- GitHub Actions
- Docker Hub
- AWS EC2
- Linux
- SSH

---

## Project Structure

```
.
├── src/
├── Dockerfile
├── pom.xml
├── .github/
│   └── workflows/
│       └── deploy.yml
└── README.md
```

---

## GitHub Actions Secrets

The following secrets are configured in GitHub:

| Secret | Description |
|---------|-------------|
| DOCKER_USERNAME | Docker Hub username |
| DOCKER_PASSWORD | Docker Hub password/access token |
| EC2_HOST | AWS EC2 Public IP |
| EC2_USERNAME | EC2 SSH username |
| EC2_SSH_KEY | Private SSH Key (.pem) |

---

## Docker Image

Docker Hub Repository:

```
abdulazizhussain/spring-boot-clidemo
```

---

## Deployment Architecture

```
Developer
    │
    ▼
Git Push
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├── Build Spring Boot
    ├── Build Docker Image
    ├── Push Image to Docker Hub
    ▼
AWS EC2
    │
    ├── Pull Latest Image
    ├── Stop Old Container
    └── Run New Container
```

---

## How to Trigger Deployment

Any push to the `main` branch automatically triggers the CI/CD pipeline.

```bash
git add .
git commit -m "Updated application"
git push origin main
```

GitHub Actions will handle the build and deployment automatically.

---

## Outcome

This project demonstrates an automated CI/CD pipeline that eliminates manual deployment steps by integrating GitHub Actions, Docker, Docker Hub, and AWS EC2. Every code change pushed to the `main` branch is automatically built, containerized, published, and deployed to an EC2 instance, ensuring fast and consistent application delivery.
