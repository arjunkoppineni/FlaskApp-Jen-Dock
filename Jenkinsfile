pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'harishkoppineni/flask-app:latest'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git url: 'https://github.com/arjunkoppineni/docker-jenkins.git', branch: 'main'
                echo "✅ Repository Cloned Successfully"
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "🔨 Building Docker Image..."
                bat "docker build -t %DOCKER_IMAGE% ."
            }
        }

        stage('Push Docker Image') {
            steps {
                echo "🚀 Pushing Docker Image..."
                withDockerRegistry([credentialsId: 'docker-hub-cred', url: 'https://index.docker.io/v1/']) {
                    bat "docker push %DOCKER_IMAGE%"
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "🚀 Running Docker Container..."
                bat "docker stop flask-app || exit 0" // Stop container if already running
                bat "docker rm flask-app || exit 0"   // Remove container if exists
                bat "docker run -d -p 5000:5000 --name flask-app %DOCKER_IMAGE%"
            }
        }
    }

    post {
        success {
            echo "🎯 Pipeline Executed Successfully!"
        }
        failure {
            echo "❌ Pipeline Failed!"
        }
    }
}
