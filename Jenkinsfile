pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting code from GitHub'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage started'
                bat 'echo Building application...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running quality checks'

                bat '''
                echo Running tests...
                exit /b 0
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage started'
                bat 'echo Deploying application...'
            }
        }
    }

    post {
        success {
            echo 'QUALITY GATE PASSED'
        }
        failure {
            echo 'QUALITY GATE FAILED - DEPLOYMENT STOPPED'
        }
    }
}
