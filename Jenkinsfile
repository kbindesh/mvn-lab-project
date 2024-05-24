pipeline {
  agent any
  stages {
    stage('SonarQube analysis') {
      environment {
        scannerHome = tool 'bin-sonar-scanner'
      }
      steps{
        withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
          sh "${scannerHome}/bin/sonar-scanner"
        }
      } 
    }
  }
}
