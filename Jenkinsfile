pipeline {
    agent any

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    sh 'cd backend && npm install'
                    sh 'cd frontend && npm install'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                script {
                    sh 'cd frontend && npm run build'
                }
            }
        }

        stage('Start Servers') {
            steps {
                script {
                    sh 'cd backend && npm start &'
                    sh 'cd frontend && npm start &'
                }
            }
        }
    }
}
