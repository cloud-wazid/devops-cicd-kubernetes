# DevOps CI/CD with Kubernetes

A CI/CD pipeline that builds a containerized web app, pushes the image to Docker Hub and deploys it to a local Kubernetes (Minikube) cluster using Jenkins.

## Tech Used
Jenkins, Docker, Docker Hub, Kubernetes (Minikube), kubectl, Git/GitHub

## Project Structure
- `index.html` – the web app
- `Dockerfile` – container image definition
- `deployment.yaml` – Kubernetes Deployment
- `service.yaml` – Kubernetes Service to expose the app
- `Jenkinsfile` – CI/CD pipeline definition

## Pipeline Flow
Git push → Jenkins pipeline → Docker image build → push to Docker Hub → deploy to Kubernetes (Minikube)

Pipeline stages: <Checkout, Build image, Push to Docker Hub, Deploy to Kubernetes>

## Run Manually
git clone https://github.com/cloud-wazid/devops-cicd-kubernetes.git
cd devops-cicd-kubernetes
docker build -t <dockerhub-username>/<image-name> .
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
minikube service <service-name>

## Verify
kubectl get pods
kubectl get svc

## Issues Solved
- Fixed the Jenkins pipeline's Kubernetes deployment step
- Set up Docker Hub credentials in Jenkins for image push
