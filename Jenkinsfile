pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checkout stage'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t devops-app:v1 .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }

        stage('Verify Deployment') {
            steps {
                bat 'kubectl get pods'
                bat 'kubectl get svc'
            }
        }
    }
}