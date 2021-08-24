pipeline {
  agent any
  stages {
    stage('SCM') {
      steps {
        echo 'Checkout master branch'
        checkout scm
      }
    }
    stage('NPM Install') {
      steps {
        bat 'npm install'
      }
    }
    stage('Build') {
      steps {
        echo 'Building..'
        bat 'npm run build'
      }
    }
  }
  post {
    success {
      slackSend(color: '#00FF00', message: "Build Successful")
    }
    failure {
      slackSend(color: '#FF0000', message: "Build Failed")
    }
  }
  
}
