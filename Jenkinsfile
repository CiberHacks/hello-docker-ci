pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/CiberHacks/hello-docker-ci.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t hello-ci:${BUILD_NUMBER} .'
            }
        }

        stage('Test Image') {
            steps {
                sh 'docker images'
            }
        }
    }
}

