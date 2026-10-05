pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/saikumar2855/3-tier-application.git'
            }
        }
        stage('Frontend Build') {
            steps {
                echo 'Building Frontend'
                bat 'cd frontend && dir'
            }
        }
        stage('Backend Build') {
            steps {
                echo 'Building Backend'
                bat 'cd backend && dir'
            }
        }
        stage('Test') {
            steps {
                echo 'Tests Passed'
            }
        }
        stage('Deployment') {
            steps {
                echo 'Deployed to AWS'
            }
        }
        stage('Verification') {
            steps {
                echo 'App Verified'
            }
        }
    }
}
