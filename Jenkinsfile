pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        print "Checkout"
        checkout([
          $class: 'GitSCM',
          branches: [[name: '*/main']],
          doGenerateSubmoduleConfigurations: false,
          userRemoteConfigs: [[credentialsId: 'nawarat', url: 'https://github.com/NawratvPatnantaporn/CSI403.git']]
        ])
      }
    }
    stage('Build') {
      steps {
        print "Hello Build"
      }
    }
    stage('Test') {
      steps {
        print "Hello Test"
      }
    }
  }
}