pipeline {
    agent any
stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/johnmoses/jenkins-docker-flask', branch: 'main'
            }
        }
stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-api .'
            }
        }
stage('Run Docker Container') {
            steps {
                sh '''
                docker stop flask-api || true
                docker rm flask-api || true
                docker run -d -p 8000:8000 --name flask-api flask-api
                '''
            }
        }
    }
}