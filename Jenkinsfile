pipeline {
    agent {
        label 'linux-agent'
    }

    environment {
        APP_NAME = 'My-C-Application'
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
                sh 'gcc new_pipeline.c -o build/new_pipeline'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'build/new_pipeline', fingerprint: true
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

        stage('Environment Test') {
            steps {
                echo "Application Name: ${APP_NAME}"
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully'
        }

        failure {
            echo 'Build failed'
        }

        always {
            echo 'Pipeline execution finished'
        }
    }
}
