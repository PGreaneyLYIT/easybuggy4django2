pipeline {
  agent any
  tools {jdk "java11"}
  stages {
    stage('SCM') {
      steps {
        node('checkout') {
          checkout scm
        }
      }
    }
    stage('SonarQube Analysis') {
      steps {
        def scannerHome = tool 'SQScanner';
        withSonarQubeEnv(installationName: 'SonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}