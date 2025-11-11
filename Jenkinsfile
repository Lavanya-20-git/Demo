pipeline {
    agent any

    environment {
        APP_NAME = "SamplePythonApp"
        DEPLOY_DIR = "/var/www/${APP_NAME}"  // Change to your deploy path
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub...'
                git branch: 'main', url: 'https://github.com/Lavanya-20-git/Demo.git'
            }
        }

        stage('Setup Python Environment') {
            steps {
                echo 'Setting up Python environment...'
                sh 'python3 -m venv venv'
                sh './venv/bin/pip install --upgrade pip'
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './venv/bin/pytest tests/'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh "mkdir -p ${DEPLOY_DIR}"
                sh "cp -r * ${DEPLOY_DIR}"
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
