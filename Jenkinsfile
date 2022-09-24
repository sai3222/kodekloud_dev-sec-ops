pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
	      archeive 'target/*.jar'
            }
      } 

      stage ('unit test -junit and jacaco') {
          steps {
	      sh "mvn test"
	  }
	  post {
	     always {
	        junit 'target/surefire-reports/*.xml'
		jacaco execPattern: 'target/jacoco.exec'
	     }	
      	  }
     }		  
    }
}
