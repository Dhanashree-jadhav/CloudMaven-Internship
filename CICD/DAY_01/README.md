# CI/CD - Day 1

## Task 1: Problems Without CI/CD

4 major risks/problems:

1.Human Errors

Manual steps can lead to mistakes (wrong files, missed steps, wrong configs).

2.Inconsistent Deployments

Different environments (dev, test, prod) may not match → “works on my machine” issue.

3.Slow Deployment Process

Takes more time because everything is done manually → delays releases.

4.No Automated Testing
Bugs may reach production because tests are not automatically executed.

 ## Conclusion 
No rollback mechanism
Difficult to track changes
High downtime risk
     
 
---

## Task 2: GitHub Actions Observation

### What triggered the workflow?
The workflow is triggered when code is pushed to the repository (push event).

### What jobs are running?
Jobs include build, install dependencies, and run tests.

### What is the workflow trying to achieve?
It automates building and testing of the application to ensure code quality.

---

## Task 3: CI/CD Pipeline Order

1. Write Code
2. Build Application
3. Run Tests
4. Deploy Application
5. Monitor Application

Developers write code
Code is built into an application
Tests are executed to check quality
Application is deployed
Monitoring ensures system health

---

## CI Pipeline Implementation (Practical)

### What I Did:
- Created GitHub Actions workflow (ci.yml)
- Configured pipeline to trigger on push to main branch
- Used ubuntu-latest runner
- Implemented build and test steps

### Workflow Steps:
1. Checkout code
2. Show project files
3. Build step
4. Test step

### Result:
- CI pipeline executed successfully
- All steps completed successfully
- Execution time: ~6 seconds

# CI/CD Pipeline - Node.js Project
## 📌 What is CI/CD?

CI/CD stands for:

Continuous Integration (CI): Automatically builds and tests code when changes are pushed
Continuous Deployment (CD): Automatically prepares or deploys the application

The main goal is to automate the software delivery process and reduce manual work.

## ⚙️ CI/CD in My Project

In this project, I implemented a CI/CD pipeline for a Node.js application using:

GitHub Actions
Docker
Docker Hub

Whenever code is pushed to the repository, the pipeline runs automatically.

# 🔄 Pipeline Flow
Developer → Push Code → GitHub Actions Triggered
→ Checkout Code → Build Docker Image
→ Login to Docker Hub → Push Image
→ Application Ready for Deployment
🛠️ Step-by-Step Explanation
# 1. Code Push (Trigger)

When code is pushed to the main/master branch, the workflow starts automatically.

on:
  push:
    branches: [ main ]
# 2. Continuous Integration (CI)
Checkout the latest code
Build Docker image
docker build -t username/node-js-app:latest .

This ensures the app runs in a consistent environment.

# 3. Authentication

The pipeline logs into Docker Hub using GitHub Secrets.

docker login
# 4. Continuous Deployment (CD)
Push Docker image to Docker Hub
docker push username/node-js-app:latest

Now the application is ready for deployment.

✅ Benefits
Automates build and deployment
Reduces manual errors
Ensures consistent environments
Faster development and release
🎯 Short Interview Explanation

In my project, I used GitHub Actions to implement CI/CD. When code is pushed, the pipeline automatically builds a Docker image for the Node.js application and pushes it to Docker Hub. This automates the build and deployment process and ensures consistency.

flowchart TD
    A[Developer] -->|Push Code| B[GitHub Repository]
    B -->|Trigger Workflow| C[GitHub Actions Pipeline]
    
    C --> D[Checkout Code]
    C --> E[Build Docker Image]
    C --> F[Login to Docker Hub]
    F --> G[Push Image]
    
    G --> H[Docker Hub (Registry)]
    H --> I[Application Ready for Deployment]
