pipeline {
  agent any

  stages {
      stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              //archive 'target/*.jar' //so that they can be downloaded later yes
            }
      } 

      stage ('unit test -junit and jacaco') {
          steps {
	      sh "mav test"
	  }
	  post {
	     always {
	        junit 'target/surfire-reports/*.xml'
		jacaco-execPattern: 'target/jacaco.exec'
	     }	
      	  }
     }		  
    }
}
