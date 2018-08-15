pipeline {
  agent any
  stages {
    stage('Monitor') {
      steps {
        git(url: 'https://github.com/akthem/heim.git', branch: 'master', changelog: true, credentialsId: '@akthem1', poll: true)
      }
    }
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            bat(script: 'D:/Dev/batchs/build.bat', returnStatus: true, returnStdout: true)
          }
        }
        stage('Unit Test') {
          steps {
            bat(script: 'D:\\Dev\\batchs\\UnitTest.bat', returnStatus: true, returnStdout: true)
          }
        }
        stage('End To End tests') {
          steps {
            bat(script: 'D:\\Dev\\batchs\\e2e.bat', returnStatus: true, returnStdout: true)
          }
        }
        stage('generate Documentation') {
          steps {
            bat(script: 'D:\\Dev\\batchs\\documentation', returnStatus: true, returnStdout: true)
          }
        }
      }
    }
    stage('Deploy Test Env') {
      parallel {
        stage('Deploy') {
          steps {
            bat(script: 'D:\\Dev\\batchs\\depoly.bat', returnStatus: true, returnStdout: true)
          }
        }
        stage('Deploy Production Env') {
          steps {
            writeFile(encoding: 'utf-8', file: 'DeploymentPROD.txt', text: 'This is a deployment in Production')
          }
        }
        stage('RollOut Deployment') {
          steps {
            writeFile(file: 'RollOut.txt', text: 'This is a rollout proof of concept', encoding: 'utf-8')
          }
        }
        stage('Archiv Artefact') {
          steps {
            writeFile(file: 'Archiv.txt', text: 'this is an archiv proof of concept', encoding: 'utf-8')
          }
        }
      }
    }
    stage('Serve Local') {
      steps {
        bat(script: 'D:\\Dev\\batchs\\serve.bat', returnStatus: true, returnStdout: true)
      }
    }
  }
}