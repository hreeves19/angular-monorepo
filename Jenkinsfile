pipeline {
    agent {
        docker {
            image 'cypress/base:20.14.0'
            // Run the container on the node specified at the
            // top-level of the Pipeline, in the same workspace,
            // rather than on a new node entirely:
            reuseNode true
        }
    }

    tools {nodejs "Node"}

    environment {
        CHROME_BIN = '/bin/google-chrome'
    }

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npx nx lint'
            }
        }
        stage('Jest Test') {
            steps {
                sh 'npm run test:ci'
            }
        }
        stage('e2e Tests') {
            steps {
                sh 'npm ci'
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