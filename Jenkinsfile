pipeline {
    agent any
    environment {
        DOCKER_CREDS = credentials('docker-credentials')
        }
        stages {
            stage('Build') {
                agent {
                    docker {
                    image 'maven:3.6.3-openjdk-11-slim'
                    }
                }
                steps {
                    script {
                    sh 'java -version'
                    sh 'mvn -version'
                    sh 'mvn verify'
                    sh 'mvn clean package'
                    sh 'ls -l target/'
                    }
                }
                post {
                    success {
                    archiveArtifacts artifacts: 'target/labmaven-*.jar', fingerprint: true, onlyIfSuccessful: true
                    }
                }
            }
        }
}