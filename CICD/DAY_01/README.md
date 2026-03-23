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
