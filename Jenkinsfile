pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aa-nadim/flask-hello-world.git'
            }
        }

        stage('Build and Run with Docker Compose') {
            steps {
                sh 'docker-compose down'  // Stop and remove existing containers
                sh 'docker-compose up --build -d'  // Rebuild and start containers in detached mode
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded! Flask app is updated and running.'
        }
        failure {
            echo 'Pipeline failed. Check the logs for errors.'
        }
    }
}