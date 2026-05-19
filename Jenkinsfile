pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "mayurg74/java-devops-app"
    }

    stages {

        stage('Clone Code') {
            steps {
                echo 'Pulling Code From GitHub'
            }
        }

        stage('Build Java Application') {
            steps {
                sh 'javac src/Main.java'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_PASS'
                )]) {

                    sh """
                    echo \$DOCKER_PASS | docker login -u \$DOCKER_USER --password-stdin
                    """
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push $DOCKER_IMAGE'
            }
        }
    }
}
