pipeline {
  agent any
  tools {jdk "java11"}
  stages {
    stage('SCM') {
      steps {
        node {
          checkout scm
        }
      }
    }
    stage('SonarQube Analysis') {
      steps {
        def scannerHome = tool 'SQScanner';
        withSonarQubeEnv() {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}