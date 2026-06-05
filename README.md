# Flask Redis Application with Docker, Jenkins and Kubernetes

# Project Overview

This project is a containerized Flask application integrated with Redis. The application demonstrates a complete DevOps deployment workflow using GitHub, Jenkins, Docker, and Kubernetes.

The main goal of this project is to understand how a Python Flask application can be developed, containerized, pushed through a CI/CD pipeline, and deployed on a Kubernetes cluster.

# Tech Stack

* Python
* Flask
* Redis
* Docker
* Kubernetes
* Jenkins
* GitHub
* Linux

# Features

* Flask-based web application
* Redis integration for caching or data storage
* Dockerized frontend/backend application
* Kubernetes deployment using YAML manifests
* Jenkins CI/CD pipeline for automated build and deployment
* GitHub repository integration

# Project Architecture

GitHub Repository
        |
        v
Jenkins Pipeline
        |
        v
Docker Build
        |
        v
Docker Image Push
        |
        v
Kubernetes Deployment
        |
        v
Flask App + Redis Service

# Folder Structure

flask-redis-project/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│
├── Dockerfile
├── Jenkinsfile
├── k8s/
|   ├── namespace.yaml
│   ├── flask-deployment.yaml
│   ├── flask-service.yaml
│   ├── redis-deployment.yaml
│   └── redis-service.yaml
│
└── README.md


# Prerequisites

Before running this project, make sure the following tools are installed:

* Git
* Docker
* Kubernetes or Minikube
* kubectl
* Jenkins
* Python 3

# Jenkins CI/CD Pipeline

The Jenkins pipeline performs the following steps:

1. Pulls the latest code from GitHub
2. Builds the Docker image
3. Pushes the image to Docker Hub or a private/public registry
4. Deploys the application to Kubernetes
5. Verifies the deployment status

Example pipeline stages:

Checkout Code
Build Docker Image
Push Docker Image
Deploy to Kubernetes
Verify Deployment


# Environment Variables

| Variable   | Description            |
| ---------- | ---------------------- |
| FLASK_ENV  | Flask environment mode |
| REDIS_HOST | Redis service hostname |
| REDIS_PORT | Redis port             |
| APP_PORT   | Flask application port |

# Useful Kubernetes Commands

kubectl get all -n flask-redis
kubectl get pods -n flask-redis
kubectl get depoyment -n flask-redis
kubectl get svc -n flask-redis
kubectl describe pod <pod-name> -n flask-redis
kubectl logs <pod-name> -n flask-redis

# Troubleshooting

# Redis connection failed

Check if the Redis pod and service are running:

kubectl get pods -n flask-redis
kubectl get svc -n flask-redis

# Flask pod not starting

Check pod logs:

kubectl logs <flask-pod-name>

# ImagePullBackOff error

Make sure the Docker image exists in the registry and Kubernetes has access to pull it.

# Jenkins deployment failed

Check Jenkins console output and verify Docker, kubectl, and Kubernetes credentials are configured correctly.

# Future Improvements

* Add Nginx reverse proxy
* Add monitoring using Prometheus and Grafana
* Add logging using Loki or ELK stack
* Add Helm chart for Kubernetes deployment
* Add production-ready secrets management
* Add automated testing in Jenkins pipeline

# Author

Created by: Yogesh Pisal

GitHub: https://github.com/Yogeshpisal216/Flask-Redis-Project.git
