pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
        sh 'npm run build'
      }
    }
    stage('Deploy') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker-credentials') {
            docker.image('node:12.13-alpine').pull()
          }
          sh 'docker build -t my-react-app .'
          sh 'docker run -d -p 3000:3000 my-react-app'
        }
      }
    }
  }
}
