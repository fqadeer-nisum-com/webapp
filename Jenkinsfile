pipeline {
  agent any
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
   	}
}
