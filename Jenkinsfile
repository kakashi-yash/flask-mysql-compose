pipeline {
    agent any
    
    stages {
        stage('Clean Old Deployment') {
            steps {
                // Use 'bat' for native Windows execution
                bat 'docker compose down'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                bat 'docker compose up -d --build'
            }
        }

        stage('Verify Health') {
            steps {
                // Sleep 15 seconds, then test endpoint using PowerShell
                sleep 15
                powershell 'Invoke-RestMethod -Uri http://localhost:5000/health'
            }
        }
    }
}