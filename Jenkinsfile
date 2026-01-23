pipeline {
    agent any

    stages {

        stage('Clone Repo') {
            steps {
                git branch: 'main',
                url: 'https://github.com/prashantgohel321/DevOps-Project-Two-Tier-Flask-App.git'
            }
        }

        stage('Docker Cleanup') {
            steps {
                sh 'docker system prune -af || true'
            }
        }

        stage('Build & Deploy') {
            steps {
                sh '''
                docker compose down || true
                docker compose build
                docker compose up -d
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deployment Successful!"
        }
        failure {
            echo "❌ Deployment Failed!"
        }
    }
}
