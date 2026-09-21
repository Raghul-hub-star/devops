pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t my-app:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop my-app || true'
                sh 'docker rm my-app || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    docker run -d \
                        --name my-app \
                        -p 8080:80 \
                        my-app:latest
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'docker ps'
                sh 'docker logs my-app'
            }
        }
    }
}
