# 🚀 CI/CD Reusable Workflow Assignment (GitHub Actions)

### shared-workflows repo link : https://github.com/Dhanashree-jadhav/shared-workflows.git

### use-shared-ci.yml file : https://github.com/Dhanashree-jadhav/cicd-practice/blob/main/.github/workflows/use-shared-ci.yml

## 📌 Overview

This project demonstrates how to create and use **reusable CI workflows** in GitHub Actions.
Instead of duplicating CI logic across multiple repositories, we define a shared workflow and reuse it in different projects.

---

## 🧩 Repositories Used

### 1️⃣ shared-workflows

* Contains the reusable CI workflow
* File: `.github/workflows/shared-ci.yml`
* Triggered using `workflow_call`

### 2️⃣ cicd-practice

* Main project repository
* Calls the shared workflow from `shared-workflows`
* File: `.github/workflows/use-shared-ci.yml`

---

## ⚙️ Shared Workflow (shared-workflows)

```yaml
name: Shared CI Workflow

on:
  workflow_call:

jobs:
  quality-check:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Run Basic CI Check
        run: echo "Running Shared CI Quality Check"

      - name: Setup Node
        if: hashFiles('package.json') != ''
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install Dependencies
        if: hashFiles('package.json') != ''
        run: npm install

      - name: Run Lint
        if: hashFiles('package.json') != ''
        run: npm run lint || echo "No lint script found"

      - name: Run Tests
        if: hashFiles('package.json') != ''
        run: npm test || echo "No test script found"
```

---

## 🔗 Using Shared Workflow (cicd-practice)

```yaml
name: Use Shared CI Workflow

on:
  push:
    branches:
      - main
  pull_request:

jobs:
  call-shared-workflow:
    uses: Dhanashree-jadhav/shared-workflows/.github/workflows/shared-ci.yml@main
```

---

## ▶️ How It Works

1. A push or pull request is made in `cicd-practice`
2. GitHub Actions triggers the workflow
3. The workflow calls the shared CI pipeline from `shared-workflows`
4. The shared workflow runs all quality checks

---

<img width="1917" height="962" alt="sh1" src="https://github.com/user-attachments/assets/cafaba15-0a84-429f-95aa-cfafe3837d1d" />
<img width="1915" height="972" alt="sh2" src="https://github.com/user-attachments/assets/a0563695-5d09-44a4-8eca-2ea2a2d197f3" />


## 🔄 Reusability Demonstration

* Any change in the shared workflow automatically reflects in all projects using it
* Example:

  * Update echo message in `shared-workflows`
  * Push changes
  * Trigger workflow in `cicd-practice`
  * Observe updated output in logs

---

## 🎯 Benefits of Reusable Workflows

* ✅ Avoid code duplication
* ✅ Maintain consistency across projects
* ✅ Easy to update CI pipelines centrally
* ✅ Scalable for multiple repositories

---

## 🧠 Key Concept

> **Reusable Workflows (`workflow_call`)** allow one repository to define CI logic and other repositories to use it, improving efficiency and maintainability.

---

## 📌 Conclusion

This assignment demonstrates how organizations can standardize CI/CD pipelines using reusable workflows, making DevOps practices more efficient and scalable.

---

## 👩‍💻 Author

Dhanashree Jadhav
