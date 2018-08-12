pipeline {
  agent any
  stages {
    stage('Monitor') {
      steps {
        git(url: 'https://github.com/akthem/heim.git', branch: 'master', changelog: true, credentialsId: '@akthem1', poll: true)
      }
    }
    stage('Build') {
      steps {
        sh 'sh echo "here we build the application"'
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "here the artifacts under src/dist must be migrated on the server 5 for angular application" '
      }
    }
    stage('Serve') {
      steps {
        sh 'echo "here we serve the pulled application from git locally"'
      }
    }
  }
}