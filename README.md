# Node.js "Hello World" Application Deployment

This repository contains the files and instructions to Dockerize, deploy, and manage a Node.js "Hello World" application using Kubernetes and ArgoCD.

## Prerequisites

Ensure you have the following installed:

- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [eksctl](https://docs.aws.amazon.com/eks/latest/userguide/eksctl.html)
- [Docker](https://docs.docker.com/get-docker/)
- [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- [Helm](https://helm.sh/docs/intro/install/)
- [ArgoCD](https://argo-cd.readthedocs.io/en/stable/getting_started/)

## 1. Dockerization

### Dockerfile

A multi-stage Dockerfile is used to build an efficient Docker image for the Node.js "Hello World" application. The Dockerfile can be found in this repository.

### Docker Image

The Docker image for this application is available on DockerHub: [docker.io/mohammadimran0186/task1](https://hub.docker.com/r/mohammadimran0186/task1)

### CI/CD with GitHub Actions

The repository is configured to use GitHub Actions for continuous integration. Any changes made in the repository will trigger a build and push the updated Docker image to DockerHub.

#### GitHub Actions Configuration

1. Generate a token from DockerHub:
   - Go to DockerHub account settings -> Security -> New Access Token -> Create.

2. Set up GitHub Secrets:
   - Go to GitHub repository settings -> Security -> Secrets and variables -> Secrets -> New repository secret.
   - Add the following secrets:
     - `DOCKERHUB_USERNAME`: Your DockerHub username.
     - `DOCKERHUB_TOKEN`: Your DockerHub access token.

## 2. Kubernetes Deployment

### Helm Chart

A Helm chart is used to deploy the Node.js application on a Kubernetes cluster. The Helm chart and necessary Kubernetes manifests are included in this repository.

### ArgoCD for GitOps Management

ArgoCD is used to manage the deployment of the application in a GitOps manner.

#### ArgoCD Installation and Configuration

1. [Install ArgoCD](https://argo-cd.readthedocs.io/en/stable/getting_started/).

2. Create a new application in ArgoCD:
   - Application Name: `node-app`
   - Project Name: `default`
   - Sync Policy: `automatic`
   - Repository URL: `https://github.com/mohammadimran0186/bansira-task`
   - Path: `node-app`
   - Cluster: `self cluster`
   - Namespace: `default`

3. Click on `Create`.

### Accessing the Application

After deployment, you can access the application using the Node public IP followed by the port number.

## Deployment Instructions

### Clone the Repository

```bash
git clone https://github.com/mohammadimran0186/bansira-task
cd bansira-task
```

### Install Necessary Packages

Refer to the links provided in the prerequisites section to install and configure the necessary tools.

### Deploy Using ArgoCD

1. Install and configure ArgoCD following the [official guide](https://argo-cd.readthedocs.io/en/stable/getting_started/).

2. Create a new application in ArgoCD with the provided repository URL and path.

3. Sync the application in ArgoCD to deploy it on your Kubernetes cluster.

### Environment Variables and Configuration

Ensure all necessary environment variables and configurations are set up as described above for DockerHub and GitHub Actions.

## Conclusion

This repository contains everything you need to Dockerize, deploy, and manage a Node.js "Hello World" application on Kubernetes using Helm and ArgoCD. Follow the instructions carefully to ensure a smooth deployment.

For any issues or queries, please open an issue in this repository.
