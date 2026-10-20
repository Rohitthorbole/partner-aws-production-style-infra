# Pipeline for building and testing the infrastructure code

pipeline {
    agent any

    stages {
        stage('initialize') {
            steps {
                // Checkout the code from the repository
                sh 'git checkout main'
                terraform init
            }
        }

        stage('Build') {
            steps {
                // Build the application
                sh 'make build'
            }
        }

        stage('Test') {
            steps {
                // Run tests
                sh 'make test'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application
                sh 'make deploy'
            }
        }
    }

    post {
        always {
            // Clean up workspace after build
            cleanWs()
        }
    }
}