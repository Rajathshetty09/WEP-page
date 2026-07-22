pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/Rajathshetty09/WEP-page.git'
            }
        }

        stage('Build Docker Images') {
            steps {
                echo 'Building container images with Docker Compose...'
                sh 'docker compose build'
            }
        }

        stage('Deploy Application') {
            steps {
                echo 'Deploying application containers...'
                // Stop older container instances if running, then launch updated containers
                sh 'docker compose down || true'
                sh 'docker compose up -d'
            }
        }
    }

    post {
        success {
            echo 'Deployment completed successfully!'
        }
        failure {
            echo 'Deployment failed. Checking docker logs...'
            sh 'docker compose logs --tail=50'
        }
    }
}
