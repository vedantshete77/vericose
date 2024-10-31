pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/vedantshete77/vericose', branch: 'main'
            }
        }
        
        stage('Install Backend Dependencies') {
            steps {
                dir('backend') {
                    script {
                        if (isUnix()) {
                            sh 'npm install'
                        } else {
                            bat 'npm install'
                        }
                    }
                }
            }
        }
        
        stage('Install Frontend Dependencies') {
            steps {
                dir('frontend') {
                    script {
                        if (isUnix()) {
                            sh 'npm install'
                        } else {
                            bat 'npm install'
                        }
                    }
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    script {
                        if (isUnix()) {
                            sh 'npm run build'
                        } else {
                            bat 'npm run build'
                        }
                    }
                }
            }
        }
        
        stage('Start Backend Server') {
            steps {
                dir('backend') {
                    script {
                        if (isUnix()) {
                            sh 'npm start'
                        } else {
                            bat 'npm start'
                        }
                    }
                }
            }
        }
        
        stage('Start Frontend Server') {
            steps {
                dir('frontend') {
                    script {
                        if (isUnix()) {
                            sh 'npm start'
                        } else {
                            bat 'npm start'
                        }
                    }
                }
            }
        }
    }
}
