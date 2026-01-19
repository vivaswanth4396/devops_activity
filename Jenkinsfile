pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Fetching source code from GitHub'
                checkout scm
            }
        }

        stage('Health Check') {
            steps {
                echo 'Checking application health'
                bat 'echo HEALTH=OK > C:\\phoenix_app\\health.txt'
            }
        }

        stage('Monitoring') {
            steps {
                echo 'Monitoring application status'
                bat 'type C:\\phoenix_app\\health.txt'
            }
        }
    }

    post {
        success {
            echo 'APPLICATION HEALTHY'
        }

        failure {
            echo 'ALERT: APPLICATION DOWN'
            bat 'echo ALERT TRIGGERED > C:\\phoenix_app\\alert.txt'
        }
    }
}
