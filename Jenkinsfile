pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'python -m py_compile app.py'

                echo 'Waiting 15 seconds before milestone...'

                sleep time: 15, unit: 'SECONDS'

                milestone(1)
            }
        }

        stage('Send Notification') {
            steps {
                echo "To: msshabreena@gmail.com"
                echo "Subject: ${env.JOB_NAME} - Build ${env.BUILD_NUMBER}"
                echo "Build URL: ${env.BUILD_URL}"
                echo "Build completed successfully."
            }
        }
    }
}
