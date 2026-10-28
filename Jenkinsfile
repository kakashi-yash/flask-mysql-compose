pipeline {
    agent any
    
    stages {
        stage('Clean Old Deployment') {
            steps {
                // If you install Jenkins natively on Windows, change 'sh' to 'bat'
                sh 'docker compose down'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                // This command reads your docker-compose.yml, builds the Flask image, and starts both containers
                sh 'docker compose up -d --build'
            }
        }

        stage('Verify Health') {
            steps {
                // Pauses to let the database initialize and checks the /health endpoint
                sleep 15
                sh 'curl -s http://localhost:5000/health'
            }
        }
    }
}