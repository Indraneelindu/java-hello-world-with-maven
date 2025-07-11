pipeline {
    agent any 
    environment {
        PATH='/opt/maven/maven/bin:$PATH'
    }
    stages {
        stage ('BUILD'){
        steps {
            echo 'The Build is Starting'
            sh 'mvn clean deploy'
            echo 'The Build is Stopped'
         }
        }
        stage ('sonarqube analysis') {
            environment {
                scannerHome = tool 'saidemy-sonar-scanner'
             }
             steps {
                 withSonarQubeEnv ('saidemy-sonarqube-server')
                 sh '${scannerHome}/bin/sonar-scanner'
              }
            }
        }
    }
