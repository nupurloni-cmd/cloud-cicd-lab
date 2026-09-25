pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t cloud-app:latest .'
            }
        }

        stage('Deploy') {
            steps {
                // Stops any old container if running, then starts the new one
                sh 'docker rm -f cloud-app || true'
                sh 'docker run -d --name cloud-app -p 5000:5000 cloud-app:latest'
            }
        }
    }
}
