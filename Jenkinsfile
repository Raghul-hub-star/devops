pipeline {
    agent any

    stages {

        stage('Clone GitHub Code') {
            steps {
                git branch: 'main',
                    url: 'http://3.80.115.176:8080/'
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
                    -p 8080:80 \
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
