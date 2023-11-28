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
                script {
                    docker.build("maryamusmani/py-auth:latest")
                }
            }
        }
 
        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    withDockerRegistry([credentialsId: 'maryamusmani', url: 'https://hub.docker.com/r/maryamusmani/py-auth']) {
                        docker.image("maryamusmani/py-auth:latest").push()
                    }
                }
            }
        }
    }
}
