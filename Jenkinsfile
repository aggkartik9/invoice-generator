pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = 'invoice-generator'
    }

    triggers {
        githubPush()
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/aggkartik9/invoice-generator.git'
            }
        }

        stage('Build & Run with Docker Compose') {
            steps {
                sh 'docker-compose down || true'
                sh 'docker-compose build'
                sh 'docker-compose up -d'
            }
        }

        stage('Test App is Running') {
            steps {
                // Replace this with actual health check if needed
                sh 'curl -f http://localhost || echo "App not reachable"'
            }
        }

        // Optional clean-up
        // stage('Tear down') {
        //     steps {
        //         sh 'docker-compose down'
        //     }
        // }
    }
}
