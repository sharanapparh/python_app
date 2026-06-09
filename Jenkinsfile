pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Python Version') {
            steps {
                sh 'python3 --version'
            }
        }

        stage('Docker Check') {
            steps {
                sh 'docker --version'
                sh 'docker ps'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:v1 .'
            }
        }

        stage('Remove Existing Container') {
            steps {
                sh 'docker rm -f flask-app || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d --name flask-app -p 5000:5000 flask-app:v1'
            }
        }

        stage('Verify Container') {
            steps {
                sh 'docker ps'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}






   





























