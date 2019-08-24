pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3002:3000'
    }

  }
  stages {
    stage('Install') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Approve') {
      when {
	branch 'production'
      }
      steps {
        input(message: 'Se aprueba?', submitter: 'fede')
      }
    }
    stage('Deploy to development') {
      when {
	branch 'development'
      }
      steps {
        echo 'Successful'
      }
    }
     stage('Deploy to production') {
      when {
	branch 'production'
      }
      steps {
        echo 'Successful'
      }
    }

  }
}
