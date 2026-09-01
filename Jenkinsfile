pipeline {
    agent {
        label 'linux-agent'
    }

    environment {
        APP_NAME = 'C-Calculator'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Compile') {
            steps {
                sh 'mkdir -p build'
                sh 'gcc calculator.c -o build/calculator'
            }
        }

        stage('Run') {
            steps {
                sh './build/calculator'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build/calculator', fingerprint: true
            }
        }

        stage('Parameter Test') {
            steps {
                echo "MESSAGE: ${params.MESSAGE}"
            }
        }

        stage('Environment Test') {
            steps {
                echo "Application Name: ${APP_NAME}"
            }
        }
    }

    post {
        success {
            echo 'Calculator build completed successfully'
        }

        failure {
            echo 'Calculator build failed'
        }

        always {
            echo 'Calculator pipeline execution finished'
        }
    }
}
