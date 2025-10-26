pipeline {
    agent {
        docker {
            image 'golang:1.22'
        }
    }

    environment {
        APP_PORT = '8081'
    }

    stages {
        stage('Build Go App') {
            steps {
                sh 'go mod tidy'
                sh 'go build -o app main.go'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t hello-world-dashboard .'
            }
        }

        stage('Run Docker Compose') {
            steps {
                sh 'docker-compose up -d --build'
            }
        }
    }

    post {
        success {
            echo '✅ Build success!'
        }
        failure {
            echo '❌ Build failed!'
        }
    }
}
