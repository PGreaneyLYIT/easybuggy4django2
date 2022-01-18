node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    tools {
        jdk "openjdk-11"
    }
    def scannerHome = tool 'SQScanner';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
}