pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/riyamaruthachalam54-web/Lakme-clone.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t lakme-clone .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop lakme-container || true'
                sh 'docker rm lakme-container || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name lakme-container lakme-clone'
            }
        }

    }
}