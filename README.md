# devops-assessment
## DevOps assessment 

\# DEVOPS.md

\## Project Overview
This project is a simple full-stack application built using a Django backend
(REST API) and a React frontend (Vite + TypeScript).  
The objective is to containerize the application, automate builds and deployment
using CI/CD.


\## Project Structure
.
├── backend/
│   ├── Dockerfile
│   └── Django source code
├── frontend/
│   ├── Dockerfile
│   └── React source code
├── docker-compose.yml
├── .github/workflows/ci-cd.yml
├── README.md


---

\## 1. Setup Guide


## Dockerization
- Separate Dockerfiles are created for frontend and backend
- Multi-stage Docker builds are used to reduce image size
- Applications run as a non-root user for better security
- .dockerignore is used to avoid unnecessary files in images
## Environment Variables
Environment variables are used to configure the application.


docker build -t devops-assessment-app .

docker run -p 3000:3000 devops-assessment-app

 
## Local Setup Instructions

1. Clone the repository  
   git clone https://github.com/Nexgensis/devops-assessment.git

2. Navigate to the project directory  
   cd devops-assessment

3. Build and run containers  
   docker-compose up --build

4. Access the application  
   - Frontend: http://localhost:3000  
   - Backend: http://localhost:8000  

Open browser at http://localhost:3000

open browser at http://localhost:8000/api/hello/

\### App running locally

!\[Local App](screenshots/app-local.png)



\### CI/CD workflow

!\[CI/CD Success](screenshots/cicd.png)



\### Server / Cloud Setup

git clone https://github.com/SalviniS/devops-assessment.git

cd devops-assessment

docker-compose up -d --build

Open deployed URL in browser



\## 2. Troubleshooting Log

Problem 1: Port 3000 in use → fix with:

netstat -ano | findstr :3000

taskkill /PID <PID> /F



Problem 2: Missing environment variables → create .env file

## CI/CD Pipeline
- CI/CD pipeline is implemented using GitHub Actions
- Pipeline triggers automatically on every push to the main branch
- Docker images are built for frontend and backend
- Images are pushed to a public container registry
- Deployment is automated after a successful build


\## 3. CI/CD Instructions

Workflow in .github/workflows/:

\- Builds Docker image

\- Runs tests

\- Deploys app

Screenshot: path/to/cicd-screenshot.png



\## 4. Terraform (Optional)

terraform init

terraform plan

terraform apply



\## 5. Submission Checklist

\- GitHub Repo: https://github.com/SalviniS/devops-assessment

\- Source code (frontend + backend)

\- Dockerfiles \& docker-compose.yml

\- .github/workflows/

\- Screenshots of app running

\- Terraform files






