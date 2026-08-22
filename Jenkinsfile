pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/dhanesh-pathare/ecommerce-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ecommerce-devops:build-${BUILD_NUMBER} .'
                sh 'docker tag ecommerce-devops:build-${BUILD_NUMBER} ecommerce-devops:latest'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop ecommerce-app || true'
                sh 'docker rm ecommerce-app || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d --name ecommerce-app -p 5000:5000 ecommerce-devops:build-${BUILD_NUMBER}'
            }
        }

        stage('Health Check') {
            steps {
                sh 'sleep 5'
                sh 'curl -f http://localhost:5000'
            }
        }
    }
}
