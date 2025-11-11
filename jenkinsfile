pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone your repository
                git branch: 'main', url: 'https://github.com/Lavanya-20-git/Demo.git'
            }
        }

        stage('Set up Python Environment') {
            steps {
                echo 'Creating virtual environment and installing dependencies...'
                // Create virtual environment
                bat 'python -m venv venv'
                // Activate and install dependencies
                bat 'venv\\Scripts\\activate && python -m pip install --upgrade pip'
                bat 'venv\\Scripts\\activate && pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running test cases...'
                bat 'venv\\Scripts\\activate && python test_app.py'
            }
        }

        stage('Run Application') {
            steps {
                echo 'Starting Flask application (for demo only)...'
                bat 'venv\\Scripts\\activate && python app.py'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deployment...'
                // Add your deployment commands here, e.g., copy files to a server
                // bat 'xcopy /Y app.py D:\\deploy\\sample-app\\'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}

