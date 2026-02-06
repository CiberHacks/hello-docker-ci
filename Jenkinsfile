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
                minikube status || minikube start --driver=none
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t hello-ci .
                '''
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                export KUBECONFIG=/var/snap/jenkins/common/.kube/config
                kubectl apply -f k8s/
                '''
            }
        }
    }
}

