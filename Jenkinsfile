//Declarative

pipeline {
  //agent any
  //agent { docker {image 'maven:3.6.3'} }
   agent { docker {image 'node:13.8'} }
  stages {
    stage('Build'){
       steps {
        // echo 'mvn --version'
        // sh 'mvn --version'
         sh 'node --version'
         echo "Build...."

	   }
	}
    stage('test'){
       steps {
         echo "test...."

	   }
	}
	stage('Integration test'){
       steps {
         echo "Integration test..."

	   }
	}
  } 
  
  post {
       always {
		  echo 'I am awesome , I always run...'
	   }
       success {
		  echo 'I run when you are successfull...'
	   }
       failure {
		  echo 'I run when you fail...'
	   }	   
  }
   

}



