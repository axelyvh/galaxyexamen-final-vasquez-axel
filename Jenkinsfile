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
                git credentialsId: 'github',
                    url: 'https://github.com/aldo2510/galaxy-jenkins-lab-maven.git',
                    branch: 'main'

                sh 'mvn -B verify'
            }
            post{
                success {
                    archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true
                }
            }
        }
        stage('SonarQube') {
            steps {
                script{
                    def scannerHome = tool 'scanner-default'
                    withSonarQubeEnv('sonar-server') {
                        sh "${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=labmaven01 \
                        -Dsonar.projectName=labmaven01 \
                        -Dsonar.sources=src/main \
                        -Dsonar.java.binaries=target/classes \
                        -Dsonar.tests=src/test"
                    }
                }
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