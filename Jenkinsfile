pipeline {

    agent any

    environment {
        IMAGE_NAME = "drishh/docker-jenkins-app"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/docker-jenkins-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t docker-jenkins-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run --rm docker-jenkins-app'
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'drishh',
                    passwordVariable: '#Password@123'
                )]) {

                    bat 'docker login -u drishh -p #Password@123'
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                bat 'docker push docker-jenkins-app'
            }
        }
    }
}