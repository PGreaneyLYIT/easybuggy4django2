pipeline {
  agent any
  tools {jdk "java11"}
  stages {
    stage('SCM') {
      steps {
        node('main') {
          checkout scm
        }
      }
    }
    stage('SonarQube Analysis') {
      environment {
        scannerHome = tool 'SQScanner'
      }
      steps {
        node('main') {
          environment {
            JAVA_HOME="${tool 'java11'}"
            PATH="${JAVA_HOME}/bin:${PATH}"
            sh 'java -version'
          }
          withSonarQubeEnv(installationName: 'SonarQube') {
            sh "${scannerHome}/bin/sonar-scanner"
          }
        }
      }
    }
  }
}