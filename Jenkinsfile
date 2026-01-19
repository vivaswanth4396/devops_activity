pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking out source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage (simulated)'
                bat 'echo Building application'
                bat 'dir'
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage (simulated)'
                bat 'echo Running tests'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy stage (simulated)'
                bat 'echo Application deployed successfully'
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished SUCCESSFULLY'
        }
        failure {
            echo 'Pipeline FAILED'
        }
    }
}
