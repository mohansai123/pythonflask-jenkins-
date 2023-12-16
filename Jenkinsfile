pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image
                    docker.build("flask-app:latest")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    // Run Docker container
                    docker.image("flask-app:latest").run("-p 5000:5000 --name flask-app-container")
                }
            }
        }
    }

    post {
        always {
            // Clean up (stop and remove) the Docker container
            script {
                docker.image("flask-app:latest").stop()
                docker.image("flask-app:latest").remove()
            }
        }
    }
}
