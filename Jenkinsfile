pipeline {
    agent any
    environment {
        DOCKER_CREDS = credentials('docker-credentials')
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo SonarQube'
            }
        }
        stage('SonarQube') {
            steps {
                sh 'echo SonarQube'
            }
        }
        stage('Build docker') {
            steps {
                sh 'echo Build Image'
            }
        }
        stage('Push docker') {
            steps {
                sh 'echo Publish Image'
            }
        }
        stage('Run Container') {
            steps {
                sh 'echo Run Container'
            }
        }
    }
}