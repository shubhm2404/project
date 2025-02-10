pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE_NAME = "ubuntu"
        DOCKER_TAG = "latest"
        DOCKER_CREDENTIALS = credentials('docker') // Your Docker credentials ID
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git 'https://github.com/shubhm2404/project.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image using Dockerfile
                    docker.build("${ubuntu}:${latest}")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push Docker image to Docker registry (e.g., Docker Hub)
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS) {
                        docker.image("${ubuntu}:${latest}").push()
                    }
                }
            }
        }
    }
    
    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Docker image build and push successful.'
        }
        failure {
            echo 'Docker image build or push failed.'
        }
    }
}
