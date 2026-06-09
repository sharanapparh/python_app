pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out code'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f flask-app || true
                docker run -d --name flask-app -p 5000:5000 flask-app:v1
                '''
            }
        }
    }
}
