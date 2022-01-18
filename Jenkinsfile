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
      def scannerHome = tool 'SQScanner';
      steps {
        withSonarQubeEnv(installationName: 'SonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}