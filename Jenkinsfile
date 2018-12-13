pipeline {
  agent any
  stages {

    stage('Build') {
      parallel {
        stage('Build 1') {
          steps {
            echo 'Build'
          }
        }
        stage('Build 2') {
          steps {
            echo 'Another Branch!'
          }
        }
      }
    }
    stage('Test 1') {
      steps {
        echo 'Test'
      }
    }
    stage('Deploy') {
      steps {
        echo 'Deploy'
      }
    }
  }
  options {
    disableConcurrentBuilds()
    buildDiscarder(logRotator(daysToKeepStr: '50', numToKeepStr: '50'))
    timeout(time: 1, unit: 'HOURS')
    parallelsAlwaysFailFast()
  }
  triggers {
    cron('*/3 * * * *')
    pollSCM('* * * * *')
  }
}