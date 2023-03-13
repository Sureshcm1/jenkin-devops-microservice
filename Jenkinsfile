//Declarative

pipeline {
  agent any
  stages {
    stage('Build'){
       steps {
         echo "Build"

	   }
	}
    stage('test'){
       steps {
         echo "test"

	   }
	}
	stage('Integration test'){
       steps {
         echo "Integration test"

	   }
	}
  } 
  
  post {
       always {
		  echo 'I am awesome , I always run'
	   }
       success {
		  echo 'I run when you are successfull'
	   }
       failure {
		  echo 'I run when you fail'
	   }	   
  }
   

}



