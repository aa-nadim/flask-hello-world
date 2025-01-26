pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aa-nadim/flask-hello-world.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker-compose build'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'echo "Running tests..."'
                // Add your test commands here (e.g., pytest)
            }
        }

        stage('Deploy Flask App') {
            steps {
                sh 'docker-compose down'  // Stop and remove existing containers
                sh 'docker-compose up -d'  // Start the Flask app in detached mode
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