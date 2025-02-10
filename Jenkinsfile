pipeline {
    agent any
	environment {
        DOCKER_CREDENTIALS = credentials('docker')  // Use the credentials ID here
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
                    // Login to Docker registry using the Docker PAT
                    docker.withRegistry('https://hub.docker.com/', DOCKER_CREDENTIALS) {
                        // Build Docker image
                        sh 'docker build -t ubuntu:latest .'
                    }
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // Push Docker image to registry
                    docker.withRegistry('https://hub.docker.com/', DOCKER_CREDENTIALS) {
                        sh 'docker push ubuntu:latest'
                    }
                }
            }
        }
	
        stage('Test') {
            steps {
                echo 'Testing...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
            }
        }
    }
}

