pipeline {
    agent any

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
        // ... lanjutkan stage lain
    }
}
