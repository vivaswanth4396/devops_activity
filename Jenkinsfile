pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Fetching source code'
                checkout scm
            }
        }

        stage('Ensure Directories') {
            steps {
                echo 'Ensuring required directories exist'

                bat '''
                if not exist C:\\phoenix_app mkdir C:\\phoenix_app
                if not exist C:\\phoenix_logs mkdir C:\\phoenix_logs
                '''
            }
        }

        stage('Ensure Configuration') {
            steps {
                echo 'Ensuring configuration file state'

                bat '''
                echo APP_NAME=PhoenixApp > C:\\phoenix_app\\config.txt
                echo ENV=production >> C:\\phoenix_app\\config.txt
                echo LOG_PATH=C:\\phoenix_logs >> C:\\phoenix_app\\config.txt
                '''
            }
        }

        stage('Verify Configuration') {
            steps {
                echo 'Verifying configuration state'

                bat '''
                type C:\\phoenix_app\\config.txt
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying application'

                bat '''
                echo Deployment done successfully > C:\\phoenix_app\\deploy.txt
                '''
            }
        }
    }

    post {
        success {
            echo 'CONFIGURATION MANAGEMENT COMPLETED'
        }
        failure {
            echo 'CONFIGURATION MANAGEMENT FAILED'
        }
    }
}
