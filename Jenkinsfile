pipeline {
  agent any
  stages {
    stage('Git Checkout') {
          steps {
              script {
                  git branch: 'main',
                      url: 'https://github.com/kbindesh/mvn-lab-project.git'
              }
          }
    }

    stage("build"){
        steps {
              echo "----------- build started ----------"
            sh 'mvn clean deploy -Dmaven.test.skip=true'
              echo "----------- build complted ----------"
        }
    }
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
