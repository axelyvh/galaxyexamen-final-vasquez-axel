pipeline {
    agent any
    environment {
        DOCKER_CREDS = credentials('docker-credentials')
    }
    stages {
        stage('Build') {
            agent {
                docker { image 'maven:3.6.3-openjdk-11-slim' }
            }
            steps {
                sh 'mvn package'
                sh 'echo "Listar RUTA"'
                sh 'ls -l target/'
            }
            post{
                success {
                    archiveArtifacts artifacts: 'target/labmaven-*.jar', fingerprint: true, onlyIfSuccessful: true
                }
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