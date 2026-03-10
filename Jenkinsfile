pipeline {
    agent any

    environment {
        IMAGE_NAME = "madhumitha3199/devops-python-app"
    }

    stages {

        stage('Clone Repository') {
             steps{
                 git branch: 'main', url: 'https://github.com/RPMadhumitha/devops-python-k8s.git'
                }
}

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $IMAGE_NAME:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'
                sh 'kubectl apply -f k8s/service.yaml'
            }
        }

    }
}