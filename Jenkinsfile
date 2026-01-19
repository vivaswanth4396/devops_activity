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

                bat '''
                if exist C:\\phoenix_app\\deploy.txt (
                    copy C:\\phoenix_app\\deploy.txt C:\\phoenix_app\\deploy_backup.txt
                )
                '''
            }
        }

        stage('Deploy New Version') {
            steps {
                echo 'Deploying new version'

                bat '''
                echo Deploying version 2 > C:\\phoenix
