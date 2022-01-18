pipeline {
  agent any
  tools {
        jdk 'java11'
    }
  stages{
    node{
      stage('SCM') {
        checkout scm
      }
      stage('SonarQube Analysis') {
        def scannerHome = tool 'SQScanner';
        withSonarQubeEnv() {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}