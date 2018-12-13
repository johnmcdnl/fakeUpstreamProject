pipeline {
  agent any
  stages {

    stage('Build') {
      parallel {
        stage('Build Stage 1') {
          steps {
            echo 'Build 1'
          }
        }
        stage('Build Stage 2') {
          steps {
            echo 'Build 2'
          }
        }
      }
    }
    stage('Test') {
     parallel {
        stage('Test Stage 1') {
          steps {
            echo 'Test 1'
          }
        }
        stage('Test Stage 2') {
          steps {
            echo 'Test 2'
          }
        }
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
    cron('*/2 * * * *')
    pollSCM('* * * * *')
  }
}