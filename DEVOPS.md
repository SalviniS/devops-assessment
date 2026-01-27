\# DEVOPS.md



\## 1. Setup Guide

\### Local Setup

git clone https://github.com/SalviniS/devops-assessment.git

cd devops-assessment

docker build -t devops-assessment-app .

docker run -p 3000:3000 devops-assessment-app

Open browser at http://localhost:3000

docker-compose up --build (if using)



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

Include screenshot/output



\## 5. Submission Checklist

\- GitHub Repo: https://github.com/SalviniS/devops-assessment

\- Source code (frontend + backend)

\- Dockerfiles \& docker-compose.yml

\- .github/workflows/

\- Screenshots of app running

\- Terraform files (if used)





