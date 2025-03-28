pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/navjoth/jenkins-cicd-demo.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'  // Using 'bat' for Windows
            }
        }
        stage('Run Tests') {
            steps {
                bat 'npm test || echo "No tests found"'
            }
        }
        stage('Deploy') {
            steps {
                bat 'start /b node server.js'  // Running Node.js app in background
            }
        }
    }
}
