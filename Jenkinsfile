pipeline {

    agent any

    stages {

        stage('Checkout') {

            steps {
                checkout scm
            }

        }

        stage('Install Dependencies') {

            steps {
                sh 'npm install'
            }

        }

        stage('Docker Build') {

            steps {
                sh 'docker build -t node-app:latest .'
            }

        }

        stage('Run Container') {

            steps {

                sh '''
                docker stop node-app || true
                docker rm node-app || true

                docker run -d \
                --name node-app \
                -p 3000:3000 \
                node-app:latest
                '''
            }
        }
    }
}
