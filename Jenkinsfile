pipeline {
    agent any

    environment {
        KUBECONFIG = 'C:\\Users\\hp\\.kube\\config'
        MINIKUBE_HOME = 'C:\\Users\\hp\\.minikube'
    }

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

        stage('Load Image into Minikube') {
            steps {
                bat 'minikube profile list'
                bat 'minikube image load devops-app:v1'
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