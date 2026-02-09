pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'git@github.com:AadamDev/spotify-devops-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t aadamdev/spotify:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push aadamdev/spotify:latest'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl apply -f k8s-deployment.yaml
                kubectl apply -f k8s-service.yaml
                '''
            }
        }
    }
}
