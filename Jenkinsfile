pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'harishkoppineni/flask-app:latest'
    }

    stages {
        stage('Clone Repo') {
            steps {
                echo "📌 Cloning Repository..."
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
                withDockerRegistry([credentialsId: 'docke-hub-cred', url: 'https://index.docker.io/v1/']) {
                    bat "docker push %DOCKER_IMAGE%"
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "🚢 Running Docker Container..."
                bat """
                    docker stop flask-app || exit 0
                    docker rm flask-app || exit 0
                    docker run -d -p 5000:5000 --name flask-app %DOCKER_IMAGE%
                """
            }
        }
    }

    post {
        success {
            echo "🎯 Pipeline Executed Successfully!"
            echo "✅ Visit: http://localhost:5000"
        }
        failure {
            echo "❌ Pipeline Failed!"
        }
    }
}
