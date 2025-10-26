pipeline {
    agent any

    environment {
        APP_PORT = credentials('APP_PORT') // opsional jika ingin pakai credentials Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Go application...'
                sh 'go mod tidy'
                sh 'go build -o app main.go'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t hello-world-dashboard .'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Running docker-compose...'
                sh 'docker-compose up -d --build'
            }
        }
    }

    post {
        success {
            echo '✅ Build and deploy success!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
