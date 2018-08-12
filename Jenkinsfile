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
        sh 'sh ng build --prod'
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "hello world" '
      }
    }
    stage('Serve') {
      steps {
        sleep(time: 11111, unit: 'MINUTES')
      }
    }
  }
}