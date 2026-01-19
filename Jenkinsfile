pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Fetching source code'
                checkout scm
            }
        }

        stage('Prepare Backup') {
            steps {
                echo 'Preparing backup before deployment'
                bat 'if exist C:\\phoenix_app\\deploy.txt copy C:\\phoenix_app\\deploy.txt C:\\phoenix_app\\deploy_backup.txt'
            }
        }

        stage('Deploy New Version') {
            steps {
                echo 'Deploying new version'
                bat 'echo Deploying version 2 > C:\\phoenix_app\\deploy.txt'
            }
        }

        stage('Verify Deployment') {
            steps {
                echo 'Verifying deployment'
                bat 'exit /b 0'
            }
        }
    }

    post {
        failure {
            echo 'Deployment failed - starting rollback'
            bat 'if exist C:\\phoenix_app\\deploy_backup.txt copy C:\\phoenix_app\\deploy_backup.txt C:\\phoenix_app\\deploy.txt'
            echo 'Rollback completed'
        }

        success {
            echo 'Deployment successful - no rollback needed'
        }
    }
}
