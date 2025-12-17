pipeline {
    agent any

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-jenkins-app:1.0 .'
            }
        }

        stage('Run Flask App') {
            steps {
                sh '''
                docker rm -f flask_container || true
                docker run -d -p 5000:5000 --name flask_container flask-jenkins-app:1.0
                '''
            }
        }
    }
}
