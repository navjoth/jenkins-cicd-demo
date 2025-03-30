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
        stage('Deploy to EC2') {
            steps {
                sshagent(['your-ec2-ssh-credentials']) {
                    sh '''
                    ssh -o StrictHostKeyChecking=no ubuntu@43.204.114.152 << EOF
                    cd jenkins-cicd-demo
                    git pull origin main
                    nohup node server.js &  # or python app.py for Flask
                    EOF
                    '''
                }
            }
        }
    }
}