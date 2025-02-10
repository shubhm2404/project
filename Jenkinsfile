pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS = credentials('docker')  // Use the credentials ID here
        DOCKER_IMAGE = 'ubuntu:latest'    // Define your Docker image name and tag
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shubhm2404/project.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building.......'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Login to Docker registry using the Docker credentials
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS) {
                        // Build Docker image with a specific tag
                        sh "docker build -t ${ubuntu} ."
                    }
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Push the Docker image to the registry
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS) {
                        sh "docker push ${ubuntu}"
                    }
                }
            }
        }
    }
}
