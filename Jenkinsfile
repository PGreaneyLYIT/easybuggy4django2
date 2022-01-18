stage('SonarQube analysis') {
    tools {
        jdk "java11" // the name you have given the JDK installation in Global Tool Configuration
    }
    environment {
        scannerHome = tool 'SQScanner' // the name you have given the Sonar Scanner (in Global Tool Configuration)
    }
    steps {
        withSonarQubeEnv(installationName: 'SonarQube') {
            sh "${scannerHome}/bin/sonar-scanner -X"
        }
    }
}