# 🚀 CI/CD Pipeline with Reusable Workflows, Docker & Slack Notifications

# project repositories :
### app-repo : https://github.com/Dhanashree-jadhav/app-repo.git
### workflow-repo : https://github.com/Dhanashree-jadhav/workflow-repo.git

## 📌 Project Overview

This project demonstrates a complete CI/CD pipeline using GitHub Actions.
It uses a reusable workflow to build, scan, and push Docker images, along with Slack notifications for real-time updates.

---

## 🛠️ Tech Stack

* GitHub Actions
* Docker
* Trivy (Security Scanning)
* Slack Webhooks

---

## 📂 Project Structure

```
app-repo/
 ├── .github/workflows/reusable.yml   # Calls reusable workflow
 ├── Dockerfile
 ├── app.js
 ├── package.json

workflow-repo/
 ├── .github/workflows/docker-ci.yml  # Reusable workflow
```

---

## ⚙️ Workflow Features

### ✅ 1. Reusable Workflow

* Defined in a separate repository (`workflow-repo`)
* Triggered using `workflow_call`

### ✅ 2. Docker Build & Push

* Builds Docker image
* Tags image dynamically (prod/staging)
* Pushes to Docker Hub

### ✅ 3. Security Scan (Trivy)

* Scans Docker image for vulnerabilities
* Fails pipeline for HIGH/CRITICAL issues

### ✅ 4. Slack Notifications

* Sends success and failure messages
* Uses Slack Incoming Webhook

---

## 🔐 Secrets Required

Add these secrets in **GitHub → Settings → Secrets**:

* `DOCKER_USERNAME`
* `DOCKER_PASSWORD`
* `SLACK_WEBHOOK_URL`

---

## 🔄 Workflow Trigger

The pipeline runs on:

* Push to `main` branch
* Push to `develop` branch
* Manual trigger (`workflow_dispatch`)

---

## 🏷️ Versioning

Reusable workflow is versioned using Git tags:

```
v1.0.1
```

---

## 📢 Sample Slack Notification

✅ Success:

```
Docker image built, scanned & pushed successfully!
```

❌ Failure:

```
CI/CD pipeline failed! Check GitHub Actions logs.
```

---

## 🎯 Outcome

* Automated CI/CD pipeline setup
* Secure Docker image build process
* Real-time monitoring via Slack
* Modular and reusable workflow design

---

## 🙌 Conclusion

This project demonstrates a production-like CI/CD setup with automation, security, and monitoring using modern DevOps practices.
