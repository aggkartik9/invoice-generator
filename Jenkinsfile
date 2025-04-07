pipeline {
    agent any

    environment {
        COMPOSE_PROJECT_NAME = "react_nginx_ci"
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
                sh 'sudo docker-compose build'
            }
        }

        stage('Run Docker Container') {
            steps {
                echo '🚀 Starting container...'
                sh 'docker-compose up -d'
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

    //post {
     //   always {
      //      echo '🧹 Cleaning up containers...'
        //    sh 'docker-compose down'
       // }
    //}
}
