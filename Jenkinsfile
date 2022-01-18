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
            env.JAVA_HOME="${tool 'java11'}"
            env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
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