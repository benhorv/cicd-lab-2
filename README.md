# ArgoCD Lab Project

This is a university lab project. It shows how to use GitHub Actions and ArgoCD to automatically deploy a Python web application to a local Kubernetes cluster.

## Folders

* `app/`: Contains the Python code (`app.py`) and the `Dockerfile`.
* `helm/`: Contains the Helm configuration files (`Chart.yaml`, `values.yaml`, `deployment.yaml`, `service.yaml`).
* `.github/workflows/`: Contains the `cd.yaml` file for GitHub Actions.

## Requirements

To run this project, you need:
* Docker
* Minikube
* Kubectl
* ArgoCD (running inside Minikube)
* A GitHub account
* A Docker Hub account

## Setup Instructions

1. **Add GitHub Secrets**: Go to your GitHub repository. Go to `Settings -> Secrets and variables -> Actions`. Add two secrets:
   * `DOCKER_USERNAME`: Your Docker Hub username.
   * `DOCKER_KEY`: Your Docker Hub token.

2. **Configure ArgoCD**: Open the ArgoCD web interface. Create a new App and connect it to this GitHub repository. Set the path to the `helm/` folder.

## How it works

1. You change the Python code and push it to GitHub.
2. GitHub Actions builds a new Docker image and pushes it to Docker Hub.
3. GitHub Actions automatically updates the version number in `helm/values.yaml`.
4. ArgoCD sees the updated file in GitHub and deploys the new version to Minikube.