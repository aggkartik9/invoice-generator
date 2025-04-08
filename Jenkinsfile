pipeline {
    agent any

    environment {
        PROJECT_NAME = "react_nginx_ci"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/aggkartik9/invoice-generator.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                echo '🛠️ Building Docker image...'
                sh 'docker build -t react .'
            }
        }

        stage('Run Docker Container') {
            steps {
                echo '🚀 Starting container...'
                sh 'docker run -d -p 3000:80 react'
            }
        }

        stage('Smoke Test') {
            steps {
                echo '🔍 Running basic app health check...'
                script {
                    sleep 5 // Give Nginx time to start
                    sh 'curl -I http://localhost:3000 || true'
                }
            }
        }
    }
}
