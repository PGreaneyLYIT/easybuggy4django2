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
        JAVA_HOME="${tool 'java11'}"
        PATH="${JAVA_HOME}/bin:${PATH}"
        sh 'java -version'
      }
      steps {
        withSonarQubeEnv(installationName: 'SonarQube') {
          sh "${scannerHome}/bin/sonar-scanner"
        }
      }
    }
  }
}