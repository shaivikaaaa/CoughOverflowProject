# CoughOverflowProject
[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=18758006)
# Cloud-Based Image Analysis Service

This project demonstrates a scalable cloud application deployed on AWS using Flask, Terraform, and the overflowengine image analysis tool.

## 🔀 Branch Structure

- **Stage-1**: API development with Flask, CRUD operations, SQLite, and overflowengine integration.
- **Stage-2**: Cloud deployment with AWS ECS Fargate, Application Load Balancer, and Terraform infrastructure setup.
- **Stage-3**: Scalability enhancements using Amazon SQS, Celery for background processing, and GitHub Actions for CI/CD.

## 🌐 Features

- REST API for image analysis tasks
- SQLite for lightweight data persistence
- overflowengine for custom image processing
- Terraform for infrastructure as code
- ECS Fargate for serverless container deployment
- Celery + SQS for asynchronous task processing
- GitHub Actions for continuous integration

## 🚀 Deployment

Infrastructure is managed with Terraform. The API is containerized and deployed to AWS Fargate. Background tasks are offloaded via Celery workers connected to an SQS queue for efficient, scalable processing.

Perfect, Shaivika! Here's an updated **README** section that includes your instructions clearly and professionally, reflecting all 3 stages and their dependencies:


### 🛠️ How to Run the Project

> Each stage includes the code from the previous stages.

#### ✅ Prerequisites

* Python 3.9+
* Docker & Docker Compose
* AWS CLI configured
* Create a `credentials` file for AWS access (used in Terraform and deployment)

#### 📦 Stage-1: Local API Development

```bash
./local.sh
```

* Runs the Flask API with SQLite and overflowengine locally.

#### ☁️ Stage-2: Deploy to AWS

```bash
./deploy.sh
```

* Deploys the API to AWS ECS Fargate using Terraform.
* Make sure the `credentials` file exists with appropriate values.

#### ⚙️ Stage-3: Scalable Cloud Version

```bash
./deploy.sh
```

* Adds support for background task processing via Celery and Amazon SQS.
* Ideal for handling large image analysis workloads.

#### ⚙️ Stage-4: Testing
To run the k6 tests, , execute the following command:
1. **Copy the API endpoint**  
   After deploying your project, an API load balancer link will be generated.  
   This link can be found inside the `api.txt` file in your root directory.  
   Example:
   k6 run -e ENDPOINT=http://coughoverflow-lb-208746660.us-east-1.elb.amazonaws.com ./tests/released.js


3. **Run the k6 test using the following command**  
Replace `<YOUR_API_ENDPOINT>` with the value copied from `api.txt`:

```bash
k6 run -e ENDPOINT=<YOUR_API_ENDPOINT> ./tests/released.js

