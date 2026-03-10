pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/riyamaruthachalam54-web/Lakme-clone.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t lakme-clone .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop lakme-container || exit 0'
                bat 'docker rm lakme-container || exit 0'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run -d -p 8081:80 --name lakme-container lakme-clone'
            }
        }
    }
}