pipeline {
    agent any  // Runs on any available Jenkins agent

    environment {
        APP_NAME = "MyApp"
        DEPLOY_ENV = "staging"
    }

    stages {
        stage('Checkout') {
            steps {
                // Pull code from Git repository
                git branch: 'main', url: 'https://github.com/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}..."
                // Example: Maven build
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // Example: Run unit tests
                sh 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo "Deploying ${APP_NAME} to ${DEPLOY_ENV} environment..."
                // Example deployment command
                sh './deploy.sh'
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
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}

