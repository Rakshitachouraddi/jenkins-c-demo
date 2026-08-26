pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                sh 'gcc hello.c -o hello'
            }
        }

        stage('Run') {
            steps {
                sh './hello'
            }
        }
    }
}
