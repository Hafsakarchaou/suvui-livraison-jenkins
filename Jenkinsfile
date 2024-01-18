pipeline {
    agent any

    tools {
     maven 'Maven3'
    }
  
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Hafsakarchaou/suvui-livraison-jenkins.git']]])
            }
        }
        
       stage ('Build') {
         steps {
              sh 'mvn clean install -f pom.xml'
            }
        }
        
        stage ('Code Quality') {
        steps {
            withSonarQubeEnv('sonar-server') {
            sh 'mvn -f pom.xml sonar:sonar'
            }
      }
    }
    
            
        
    }
}