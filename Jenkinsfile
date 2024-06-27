pipeline {
    agent any
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