pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Fetching code'
                checkout scm
            }
        }

        stage('Provision Infrastructure') {
            steps {
                echo 'Provisioning infrastructure (Ansible simulation)'

                bat '''
                echo Creating application directories...
                if not exist C:\\phoenix_app mkdir C:\\phoenix_app
                if not exist C:\\phoenix_logs mkdir C:\\phoenix_logs
                '''
            }
        }

        stage('Configure Environment') {
            steps {
                echo 'Configuring environment'

                bat '''
                echo APP_ENV=production > C:\\phoenix_app\\env.txt
                echo LOG_PATH=C:\\phoenix_logs >> C:\\phoenix_app\\env.txt
                '''
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying application'

                bat '''
                echo Application deployed successfully > C:\\phoenix_app\\deploy.txt
                '''
            }
        }
    }

    post {
        success {
            echo 'INFRASTRUCTURE AUTOMATION COMPLETED'
        }
        failure {
            echo 'INFRASTRUCTURE AUTOMATION FAILED'
        }
    }
}
