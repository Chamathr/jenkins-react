pipeline {
  agent {
    docker {
      image 'node:12.13-alpine'
      args '-p 3000:3000'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
        sh 'npm run build'
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker build -t my-react-app .'
        sh 'docker run -d -p 3000:3000 my-react-app'
      }
    }
  }
}
