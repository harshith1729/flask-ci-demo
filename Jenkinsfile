pipeline {
    agent { label 'master' }
    stages {
        stage('Checkout') {
            steps {
                // IMPORTANT: Change this URL to your own GitHub repository URL
                git 'https://github.com/harshith1729/flask-ci-demo.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh '''
                python3 -m venv venv
                source venv/bin/activate
                pip install -r requirements.txt
                '''
            }
        }
        stage('Run Tests') {
            steps {
                sh '''
                source venv/bin/activate
                pytest
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh 'sudo systemctl restart flaskapp'
            }
        }
    }
}