pipeline {
    agent any

    stages {

        stage('Checkout Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/CiberHacks/hello-docker-ci.git'
            }
        }

        stage('Start Minikube') {
            steps {
                sh '''
                minikube status || minikube start --driver=docker
                '''
            }
        }

        stage('Build Docker Image in Minikube') {
            steps {
                sh '''
                eval $(minikube docker-env)
                docker build -t hello-ci .
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl apply -f k8s/
                '''
            }
        }
    }
}

