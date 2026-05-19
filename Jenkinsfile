pipeline {
    agent any

    stages {

        stage('Git Pull') {
            steps {
                echo 'Pulling Code From GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'javac src/Main.java'
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -cp src Main'
            }
        }
    }
}
