# Jenkins CI/CD Pipeline

---

## What is CI/CD?

**CI/CD (Continuous Integration / Continuous Delivery or Continuous Deployment)** is a DevOps practice that automates the software development lifecycle.

It helps developers deliver applications faster, with fewer errors and more consistent deployments.

### Continuous Integration (CI)

Continuous Integration (CI) is the process of automatically integrating code changes into a shared repository.

When a developer pushes code:

- The application is built
- Automated tests are run
- Code quality is checked
- Feedback is provided immediately

### Benefits of CI

- Detects bugs early
- Improves code quality
- Reduces manual testing
- Prevents integration issues

---

### Continuous Delivery (CD)

Continuous Delivery automatically prepares the application for deployment after all CI stages pass.

The application is ready to be released, but a person approves the deployment.

---

### Continuous Deployment

Continuous Deployment goes one step further by automatically deploying the application after successful testing, with no manual approval.

---

## CI vs CD

| Continuous Integration | Continuous Delivery / Deployment |
|-------------------------|----------------------------------|
| Build the application | Deploy the application |
| Run automated tests | Release the application |
| Validate code changes | Deliver software to users |

---

## What is Jenkins?

Jenkins is an open-source automation server used to create CI/CD pipelines.

It connects tools such as GitHub, Docker and AWS to automate repetitive development tasks.

Jenkins can:

- Build applications
- Run automated tests
- Execute scripts
- Deploy applications
- Automate software delivery

---

## How Jenkins Works

1. A developer pushes code to GitHub.
2. A GitHub webhook notifies Jenkins.
3. Jenkins starts the pipeline.
4. Jenkins builds the application.
5. Automated tests are executed.
6. If successful, Jenkins deploys the application to an EC2 instance.
7. The updated application becomes available to users.

---

# Jenkins CI/CD Pipeline Diagram

![Jenkins CI/CD Pipeline Diagram](https://github.com/user-attachments/assets/958e1b40-8754-416a-a985-499887b35dad)

---

## Jenkins Pipeline Stages

### Job 1 – Build & Test (CI)

- Clone the GitHub repository
- Install dependencies
- Build the application
- Run automated tests

If any step fails, the pipeline stops.

---

### Job 2 – Merge

If testing is successful:

- Merge the `dev` branch into `main`
- Push the updated `main` branch

---

### Job 3 – Deploy (CD)

Jenkins connects to the AWS EC2 instance using SSH.

Typical deployment tasks include:

- Pull latest code
- Install/update dependencies
- Restart the application (PM2/Docker)

---

## Jenkins Architecture

The pipeline consists of:

- **Developer** – writes and pushes code
- **GitHub Repository** – stores source code
- **Webhook** – triggers Jenkins automatically
- **Jenkins Controller (Master)** – manages pipeline execution
- **Jenkins Agent** – runs build and deployment jobs
- **AWS EC2 Instance** – hosts the application

---

## Pipeline Workflow

```text
Developer
    │
git push
    │
    ▼
GitHub Repository
    │
Webhook Trigger
    │
    ▼
Jenkins
    │
    ▼
Build
    │
    ▼
Test
    │
    ▼
Merge
    │
    ▼
Deploy
    │
    ▼
AWS EC2
    │
    ▼
Application Running
```

---

## Benefits of Using Jenkins

- Automates repetitive tasks
- Reduces manual deployment errors
- Provides fast feedback
- Improves software quality
- Supports repeatable deployments
- Integrates with GitHub, AWS, Docker and many other tools

---

## Summary

Jenkins automates the CI/CD process by detecting code changes, building and testing the application, and deploying it automatically when all stages are successful. This enables faster, more reliable, and consistent software delivery.
