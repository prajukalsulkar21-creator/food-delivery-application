pipeline {
    agent any

    stages {
        stage('Checkout GitHub') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t food-delivery-app:latest .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'docker rm -f food-delivery-app || true'
                sh 'docker run -d --name food-delivery-app --restart unless-stopped -p 80:80 food-delivery-app:latest'
            }
        }
    }
}
