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
                sh 'gcc new_pipeline -o new_pipeline'
            }
        }

        stage('Run') {
            steps {
                sh './new_pipeline'
            }
        }
    }
}
