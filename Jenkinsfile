pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
      }
    }
    stage('Input') {
      steps {
        input 'Finished using the web site? (Click "Proceed" to continue)'
      }
    }
    stage('') {
      steps {
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    Image = '-p 3000:3000'
  }
}