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
        bat(script: 'D:/Dev/projectss/batchs/build.bat', returnStatus: true, returnStdout: true)
      }
    }
    stage('Deploy') {
      steps {
        bat(script: 'd:/Dev/projectss/batches/depoly.bat', returnStatus: true, returnStdout: true)
      }
    }
    stage('Serve') {
      steps {
        bat(script: 'd:/Dev/projectss/batchs/serve.bat', returnStatus: true, returnStdout: true)
      }
    }
  }
}