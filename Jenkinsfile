pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
        DOCKERHUB_USERNAME = 'saikumar2855'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/saikumar2855/3-tier-application.git'
            }
        }
        stage('Build Backend Image') {
            steps {
                bat 'docker build -t %DOCKERHUB_USERNAME%/backend:latest ./backend'
            }
        }
        stage('Build Frontend Image') {
            steps {
                bat 'docker build -t %DOCKERHUB_USERNAME%/frontend:latest ./frontend'
            }
        }
        stage('Login to DockerHub') {
            steps {
                bat 'echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin'
            }
        }
        stage('Push Images') {
            steps {
                bat 'docker push %DOCKERHUB_USERNAME%/backend:latest'
                bat 'docker push %DOCKERHUB_USERNAME%/frontend:latest'
            }
        }
        stage('Deploy') {
            steps {
                bat 'docker-compose down || exit 0'
                bat 'docker-compose up -d'
            }
        }
    }
}