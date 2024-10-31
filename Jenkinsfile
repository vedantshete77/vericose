pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Clone the repository
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'npm install --prefix backend'
                        sh 'npm install --prefix frontend'
                    } else {
                        bat 'npm install --prefix backend'
                        bat 'npm install --prefix frontend'
                    }
                }
            }
        }
        
        stage('Build Frontend') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'npm run build --prefix frontend'
                    } else {
                        bat 'npm run build --prefix frontend'
                    }
                }
            }
        }

        stage('Start Servers') {
            steps {
                script {
                    if (isUnix()) {
                        // Start backend and frontend servers in the background on Unix
                        sh 'nohup npm run backend --prefix backend &'
                        sh 'nohup npm start --prefix frontend &'
                    } else {
                        // Start backend and frontend servers in the background on Windows
                        bat 'start /B npm run backend --prefix backend'
                        bat 'start /B npm start --prefix frontend'
                    }
                }
            }
        }
    }
}
