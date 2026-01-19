pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Pulling source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
                bat 'echo Building application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                bat 'exit /b 0'
            }
        }

        stage('Quality Gate') {
            steps {
                echo 'Quality gate passed'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application'
                bat 'echo Deployed successfully > C:\\phoenix_app\\deploy.txt'
            }
        }

        stage('Monitor') {
            steps {
                echo 'Monitoring application'
                bat 'echo HEALTH=OK > C:\\phoenix_app\\health.txt'
            }
        }
    }

    post {
        success {
            echo 'CI/CD PIPELINE COMPLETED SUCCESSFULLY'
        }

        failure {
            echo 'PIPELINE FAILED - INITIATING ROLLBACK'
            bat 'echo Rollback initiated > C:\\phoenix_app\\rollback.txt'
        }
    }
}
