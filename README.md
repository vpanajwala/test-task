# test-task
# Multi-Stage Deployment: Node.js + React.js + GitLab CI/CD + Laravel Distributed Setup

This repository contains:
1. **Dockerized Node.js & React.js** application with multi-stage build and Nginx reverse proxy.
2. **GitLab CI/CD Pipeline** for deployment using a self-hosted runner.
3. **Distributed Laravel Application Design** with Web Server, PHP-FPM, Redis, MySQL, and Elasticsearch.

---
 📦 Step 1: Dockerize Node.js & React.js App

### Directory Structure
├── backend/ # Node.js API
├── frontend/ # React.js UI
├── docker-compose.yml
├── nginx.conf
├── Dockerfile
└── .env.example

🔄 Step 2: GitLab CI/CD Pipeline

Configured in .gitlab-ci.yml.

Deploys to server via SSH using a self-hosted GitLab Runner.

Pipeline Stages:

Build → Multi-stage Docker image

Push → Push to container registry

Deploy → SSH into VM & restart containers

Run the pipeline by pushing changes to main branch:

git add .
git commit -m "Deploy update"
git push origin main

⚙️ Step 3: Distributed Laravel Setup

Services:

Nginx (Web Server)

PHP-FPM (Laravel app runtime)

Redis (Cache)

MySQL (Database)

Elasticsearch (Search engine)

Security & Scalability Features:

Reverse proxy with SSL termination

Separated DB & cache nodes

Horizontal scaling for web layer

Environment variables managed securely

Cost optimization by right-sizing resources

Example Deployment Plan:

Use docker-compose.override.yml for local dev

Use Kubernetes manifests for production

Configure persistent volumes for MySQL & Elasticsearch
🔐 Security, Scalability & Cost-Effectiveness
Security

Reverse proxy with SSL termination.

Secrets & environment variables stored securely.

Database & cache nodes separated from public access.

Scalability

Horizontal scaling for web layer.

Redis caching for faster responses.

Kubernetes manifests for production scaling.

Cost-Effectiveness

Right-sized resources for each environment.

On-demand scaling to reduce unused compute costs.

Storage optimized with persistent volumes.

📋 Example Deployment Plan:

Use docker-compose.override.yml for local development.

Use Kubernetes manifests for production.

Configure persistent volumes for MySQL & Elasticsearch.



🗂 .env File
# Backend
NODE_ENV=production
API_PORT=5000

# Frontend
REACT_APP_API_URL=http://localhost:5000

# Laravel Distributed Setup
APP_ENV=production
APP_KEY=base64:YourLaravelAppKeyHere
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel_user
DB_PASSWORD=secret
REDIS_HOST=redis
ELASTICSEARCH_HOST=elasticsearch




