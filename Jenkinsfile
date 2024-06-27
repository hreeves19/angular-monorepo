pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'nx test angular-store'
            }
            steps {
                sh 'nx e2e angular-store-e2e'
            }
        }
    }
}