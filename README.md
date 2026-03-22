DevOps Python K8s

Overview
This project demonstrates how to build a complete CI/CD pipeline for a Python Flask application using Docker, Jenkins, and Kubernetes. The repository contains the application code, containerization instructions, Kubernetes manifests, and Jenkins pipeline configuration. The goal is to show how modern DevOps practices can automate the process of building, testing, and deploying applications to a Kubernetes cluster.

Features
- Simple Python Flask web application (app.py)
- Dockerfile for containerizing the application
- Kubernetes manifests for pods, deployments, and services
- Jenkinsfile for CI/CD pipeline automation
- Example workflow from code commit to Kubernetes deployment

Architecture

1. Jenkins pipeline is triggered automatically.
2. Jenkins builds a Docker image of the Flask app.
3. The image is pushed to DockerHub.
4. Kubernetes pulls the image and deploys it using manifests.
5. The application is accessible via a Kubernetes service.

Tech Stack
- Python with Flask framework
- Docker for containerization
- Kubernetes for orchestration
- Jenkins for CI/CD automation
- GitHub for source control

Setup Instructions
1. Clone the repository:
   git clone https://github.com/RPMadhumitha/devops-python-k8s.git
   cd devops-python-k8s

2. Run locally:
   pip install flask
   python app.py
   Access the app at http://localhost:5000

3. Build and push Docker image:
   docker build -t your-dockerhub-username/devops-python-k8s:latest .
   docker push your-dockerhub-username/devops-python-k8s:latest

4. Deploy to Kubernetes:
   kubectl apply -f k8s/pod-definition.yml
   kubectl apply -f k8s/deployment.yml
   kubectl apply -f k8s/service.yml

Repository Structure
devops-python-k8s/
│── app.py                Flask application code
│── Dockerfile            Instructions to build Docker image
│── Jenkinsfile           CI/CD pipeline definition
│── requirements.txt      Python dependencies
│── k8s/
│   ├── pod-definition.yml
│   ├── deployment.yml
│   └── service.yml
└── README.md             Documentation

CI/CD Workflow

- Jenkins builds Docker image and pushes to DockerHub.
- Kubernetes manifests are applied to deploy the app.
- Application runs inside pods managed by Kubernetes.
- Service exposes the app to external users.
.

References
- Kubernetes Documentation: https://kubernetes.io/docs/home/
- Docker Documentation: https://docs.docker.com/
- Jenkins Documentation: https://www.jenkins.io/doc/
