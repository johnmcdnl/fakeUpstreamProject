pipeline {
  agent any
  stages {

    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build 1'
          }
        }
        stage('') {
          steps {
            echo 'Build 2'
          }
        }
      }
    }
    stage('Test') {
     parallel {
        stage('Test') {
          steps {
            echo 'Test 1'
          }
        }
        stage('') {
          steps {
            echo 'Test 2'
          }
        }
      }
    }
    stage('Deploy') {
     parallel {
        stage('Deploy') {
          steps {
            echo 'Deploy 1'
          }
        }
        stage('') {
          steps {
            echo 'Deploy 2'
          }
        }
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
    cron('*/1 * * * *')
    pollSCM('* * * * *')
  }
}