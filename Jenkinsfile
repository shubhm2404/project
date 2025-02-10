pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/shubhm2404/project.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building...'
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
