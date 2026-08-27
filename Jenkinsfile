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
                sh 'mkdir -p build'
                sh 'gcc new_pipeline.c -o build/new_pipeline'
            }
        }

        stage('Run') {
            steps {
                sh './build/new_pipeline'
            }
        }

        stage('Parameter Test') {
            steps {
                echo "MESSAGE: ${params.MESSAGE}"
            }
        }
    }
}
