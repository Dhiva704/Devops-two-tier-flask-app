pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/<your-username>/<your-repo-name>.git'
            }
        }

        stage('Deploy App') {
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
            echo "✅ Deployment Successful"
        }
        failure {
            echo "❌ Deployment Failed"
        }
    }
}
