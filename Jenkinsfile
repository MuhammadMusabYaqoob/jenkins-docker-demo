pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop jenkins-demo-container || true'
                sh 'docker rm jenkins-demo-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8080:80 --name jenkins-demo-container jenkins-demo:latest'
            }
        }
    }
}