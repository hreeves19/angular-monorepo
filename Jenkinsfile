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
                sh 'nx lint'
            }
        }
        stage('Jest Test') {
            steps {
                sh 'nx test angular-store'
            }
        }
        stage('e2e Tests') {
            steps {
                sh 'nx e2e angular-store-e2e'
            }
        }
        stage('Deployment') {
            steps {
                sh 'nx run-many -t build'
            }
        }
    }
}