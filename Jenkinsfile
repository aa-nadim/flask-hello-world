pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/aa-nadim/flask-hello-world.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Stop Existing Flask App') {
            steps {
                sh '''
                pkill -f "python app.py" || true
                '''
            }
        }

        stage('Run Flask App') {
            steps {
                sh 'nohup python app.py > flask.log 2>&1 &'
            }
        }
    }
}