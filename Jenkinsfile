pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'harishkoppineni/flask-app:latest'
    }

    stages {
        stage('Clone Repo') {
            steps {
<<<<<<< HEAD
                git url: 'https://github.com/arjunkoppineni/docker-jenkins.git', branch: 'main'
                echo "✅ Repository Cloned Successfully"
=======
                echo "📌 Cloning Repo..."
                git url: 'https://github.com/arjunkoppineni/docker-jenkins.git', branch: 'main'
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
>>>>>>> 969afa69cb90812e058ff68bf18406aa688e976a
            }
        }

<<<<<<< HEAD
        stage('Build Docker Image') {
            steps {
                echo "🔨 Building Docker Image..."
                bat "docker build -t %DOCKER_IMAGE% ."
            }
        }

        stage('Push Docker Image') {
            steps {
                echo "🚀 Pushing Docker Image..."
                script {
                    withDockerRegistry([credentialsId: 'docker-hub-cred', url: '']) {
                        bat "docker login -u %DOCKER_USER% -p %DOCKER_PASS%"
                        bat "docker push %DOCKER_IMAGE%"
                    }
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
=======
    post {
        success {
            echo "🎯 Pipeline Executed Successfully!"
        }
        failure {
            echo "❌ Pipeline Failed!"
        }
    }
}
>>>>>>> 969afa69cb90812e058ff68bf18406aa688e976a
