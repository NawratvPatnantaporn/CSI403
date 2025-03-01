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
        echo "Docker Build Image"
        script {
            sh "docker build -t csi403-frontend ."
            echo "Docker Build Image Success"
        }

        echo "Docker Image Run Container"
        script {
            sh "docker rm -f csi403-frontend-run || true"
            sh "docker run -d --name csi403-frontend -p 54100:3000 csi403-frontend"
            echo "Docker Image Run Container Success"
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