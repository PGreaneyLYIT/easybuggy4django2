stage('SonarQube Analysis') {
    tool name "java11"
    environment {
        scannerHome = tool 'SQScanner'
    }
    steps {
        withSonarQubeEnv(installationName: 'SonarQube') {
            sh "${scannerHome}/bin/sonar-scanner -X"
        }
    }
}