pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aa-nadim/flask-hello-world.git'
            }
        }

        stage('Build and Run with Docker Compose') {
            steps {
                sh 'docker-compose down' // Stop and remove existing containers
                sh 'docker-compose up --build -d' // Build and start containers in detached mode
            }
        }
    }
}