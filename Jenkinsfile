pipeline {
    agent any
    stages {
        stage('Build Backend') {
            steps {
                echo 'Building backend...'
                bat 'docker build -t saikumar2855/backend:latest ./backend'
            }
        }
        stage('Build Frontend') {
            steps {
                echo 'Building frontend...'
                bat 'docker build -t saikumar2855/frontend:latest ./frontend'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying 3-tier app...'
                bat 'docker-compose down || echo No containers'
                bat 'docker-compose up -d --build'
            }
        }
    }
}