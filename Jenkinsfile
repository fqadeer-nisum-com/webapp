pipeline {   
  agent any
  environment {
        MAVEN_HOME = '/root/maven/apache-maven-3.5.3'
    }
    stages {
      stage('GitHub clone') {
            steps {
                checkout scm
            }
      }
      stage('Build') {  
        steps {  
          sh "${MAVEN_HOME}/bin/mvn clean package"  
        }  
      }
      stage('Test') {
        steps {
          sh "${MAVEN_HOME}/bin/mvn clean test"
          }
      }
    } 
}
