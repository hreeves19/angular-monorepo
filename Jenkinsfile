pipeline {
    agent any

    environment {
        CHROME_BIN = '/bin/google-chrome'
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Lint') {
            steps {
                sh 'npx nx lint'
            }
        }
        stage('Jest Test') {
            steps {
                sh 'npx nx test angular-store'
            }
        }
        stage('e2e Tests') {
            agent {
                docker {
                    image 'cypress/base:20.14.0'
                    // Run the container on the node specified at the
                    // top-level of the Pipeline, in the same workspace,
                    // rather than on a new node entirely:
                    reuseNode true
                }
            }
            steps {
                sh 'npx nx e2e angular-store-e2e'
            }
        }
        stage('Deployment') {
            steps {
                sh 'npx nx run-many -t build'
            }
        }
    }
}