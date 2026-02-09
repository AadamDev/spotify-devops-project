pipeline {
  agent any

  stages {
    stage('Clone Repo') {
      steps {
        git 'https://github.com/AadamDev/spotify-devops-project.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        sh 'docker build -t spotify-clone:latest .'
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
