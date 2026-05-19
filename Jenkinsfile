pipeline {
    agent any

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
                sh 'docker build -t java-devops-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run --name java-container java-devops-app'
            }
        }
    }
}
