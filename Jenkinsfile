pipeline {
    agent any

    stages {

        stage('Clone GitHub Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Raghul-hub-star/devops.git'
            }
        }

        stage('Docker Build') {
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

        stage('Docker Run') {
            steps {
                sh '''
                    docker run -d \
                    --name my-app \
                    -p 8090:80 \
                    my-app:latest
                '''
            }
        }

        stage('Verify') {
            steps {
                sh 'docker ps'
            }
        }
    }
}
