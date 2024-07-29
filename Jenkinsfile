pipeline {
    agent any

    environment {
        DOCKER_CREDENTIALS_ID = 'dockercred'
        DOCKER_IMAGE_NAME = 'utsavshah0305/day15'
    }

    stages {
        stage('Checkout') {
            steps {
                // Clone the Git repository
                git branch: 'main',url: 'https://github.com/Utsav0701/day15.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image
                    docker.build(DOCKER_IMAGE_NAME)
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    // Log in to Docker Hub and push the image
                    docker.withRegistry('', DOCKER_CREDENTIALS_ID) {
                        docker.image(DOCKER_IMAGE_NAME).push()
                    }
                }
            }
        }
    }

    post {
        always {
            // Clean up
            echo "finish"
        }
    }
}
