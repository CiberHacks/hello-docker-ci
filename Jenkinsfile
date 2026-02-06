pipeline {
    agent any

    stages {

        stage('Checkout Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/CiberHacks/hello-docker-ci.git'
            }
        }

        stage('Build Docker Image in Minikube') {
            steps {
                script {
                    sh '''
                    eval $(minikube docker-env)
                    docker build -t hello-ci .
                    '''
                }
            }
        }

        stage('Deploy to Kubernetes (Minikube)') {
            steps {
                script {
                    sh '''
                    kubectl apply -f k8s/
                    '''
                }
            }
        }
    }
}

