# MEAN Stack CRUD App

## Tech Stack
- MongoDB, Express.js, Angular 15, Node.js
- Docker, Docker Compose, Nginx
- GitHub Actions (CI/CD)
- AWS EC2 (Ubuntu 22.04)

---

## Repository Structure
```
mean-crud-app/
├── backend/Dockerfile
├── frontend/Dockerfile
├── docker-compose.yml
├── nginx.conf
└── .github/workflows/deploy.yml
```

---

## Setup & Deployment Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/mean-crud-app.git
cd mean-crud-app
```

### 2. Build and Push Docker Images
```bash
docker build -t YOUR_DOCKERHUB_USERNAME/mean-backend:latest ./backend
docker build -t YOUR_DOCKERHUB_USERNAME/mean-frontend:latest ./frontend
docker push YOUR_DOCKERHUB_USERNAME/mean-backend:latest
docker push YOUR_DOCKERHUB_USERNAME/mean-frontend:latest
```

### 3. Deploy on AWS EC2
```bash
ssh -i your-key.pem ubuntu@YOUR_EC2_IP

docker-compose up -d
```

### 4. Access the App
Open `http://YOUR_EC2_IP` in your browser.

---

## CI/CD Pipeline

- Trigger: Push to `main` branch
- Steps: Build images → Push to Docker Hub → SSH into VM → Pull & restart containers
- Tool: GitHub Actions

---

## Nginx
Nginx runs on port 80 and proxies:
- `/` → Angular frontend (port 80)
- `/api/` → Node.js backend (port 3000)

---

## Screenshots

### 1. CI/CD Pipeline Execution
![CI/CD](<./screenshots/cicd-pipeline.png>)

### 2. Docker Image Build & Push
![Docker Push](<./screenshots/docker-push.png>)

### 3. Application UI
![App UI](<./screenshots/app-ui.png>)

### 4. Nginx & Infrastructure
![Nginx](<./screenshots/nginx-running.png>)

---