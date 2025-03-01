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
                print "Docker Build Image"
                script {
                    bat "docker build -t csi403-frontend ."
                    print "Docker Build Image Success"
                }

                print "Docker Image Run Container"
                script {
                    bat "docker rm -f csi403-frontend-run || true"
                    bat "docker run -d --name csi402-frontend -p 54100:3000 csi403-frontend"
                    print "Docker Image Run Container Success"
                }
            }
        }
    stage('Test') {
      steps {
        print "Hello Test"
      }
    }
  }
}