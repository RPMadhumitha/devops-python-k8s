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
                  withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials',
                                   usernameVariable: 'DOCKER_USER',
                                   passwordVariable: 'DOCKER_PASS')]) {
                    sh 'echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin'
                    sh 'docker push $IMAGE_NAME:latest'
                }
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl --insecure-skip-tls-verify=true apply -f k8s/deployment.yaml'
                sh 'kubectl --insecure-skip-tls-verify=true apply -f k8s/service.yaml '
            }
        }

    }
}