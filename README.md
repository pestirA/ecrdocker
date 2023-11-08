# ecrdocker
This repository contains the necessary files and configurations to deploy a Docker image to an Amazon Elastic Container Registry (ECR) using GitHub Actions. The deployed image will be stored in a repository called "artifacts," and the GitHub Actions workflow will output the defined image tag.

### Repository Files
The repository is organized as follows:

Dockerfile: This is the Dockerfile used to build the Docker image that will be deployed to ECR. You can customize this file to define the contents and configuration of your Docker image.

.github/workflows/: This directory contains the GitHub Actions workflow configuration file.

.github/workflows/deploy-to-ecr.yml: This workflow is responsible for deploying the Docker image to AWS ECR. It is triggered when you push changes to the repository.

### GitHub Actions Workflow
Workflow Steps
The workflow defined in .github/workflows/deploy-to-ecr.yml consists of the following steps:

Checkout Code: This step checks out the latest code from the repository, enabling subsequent steps to access the code and Dockerfile.

Configure AWS Credentials: Before deploying the Docker image to ECR, the workflow sets up AWS credentials using secrets stored in the GitHub repository. You must configure these secrets in your repository settings for security. The required secrets are:

AWS_ACCESS_KEY_ID: The access key ID for an AWS IAM user with permissions to interact with ECR.
AWS_SECRET_ACCESS_KEY: The secret access key corresponding to the above access key ID.
Login to AWS ECR: This step uses the AWS credentials to authenticate with AWS ECR, allowing it to push Docker images to the specified ECR repository.

Build and Push Docker Image: The workflow uses the Dockerfile to build a Docker image. You can customize this file to suit your application's needs. After successfully building the image, it pushes the image to the "artifacts" repository in your AWS ECR, with a defined image tag.

Output Image Tag: The final step of the workflow outputs the defined image tag to the GitHub Actions logs. You can use this tag in subsequent workflows or scripts as needed.

### Workflow Configuration
You can customize the workflow by modifying the .github/workflows/deploy-to-ecr.yml file in your forked repository to fit your specific needs. Be sure to update the AWS ECR repository name, Dockerfile, and any other parameters to match your project's requirements.

### Usage
To use this repository and GitHub Actions workflow for deploying a Docker image to AWS ECR:

Fork this repository to your GitHub account.

Set up the required secrets (AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY) in your forked repository's settings. 
These secrets should have AWS IAM credentials with ECR permissions.

Customize the Dockerfile in your forked repository to define the Docker image you want to build and deploy.

Push changes to your repository, and the GitHub Actions workflow will automatically trigger, deploying the Docker image to the specified AWS ECR repository and outputting the image tag.

### License
This repository is provided under the MIT License. You are free to use and modify the code as needed, but please review the license for more details on its terms and conditions.

