node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    tools {jdk "java11"}
    def scannerHome = tool 'SQScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}