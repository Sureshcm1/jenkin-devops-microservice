//Declarative

pipeline {
  agent any
  //agent { docker {image 'maven:3.6.3'} }
  // agent { docker {image 'node:13.8'} }

  environment {
    dockerHome = tool 'myDocker'
    mavenHome = tool 'myMaven'
    PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
  }
  stages {
    stage('Checkout'){
       steps {
        // echo 'mvn --version'
         sh 'mvn --version'
         sh 'docker version'
         //sh 'node --version'
         echo "Build...."
         echo "PATH - $PATH"
          echo "BUILD_NUMBER - $env.BUILD_NUMBER"
          echo "BUILD_ID - $env.BUILD_ID"
          echo "JOB_NAME - $env.JOB_NAME"
          echo "BUILD_TAG - $env.BUILD_TAG"
          echo "BUILD_URL - $env.BUILD_URL"

	   }
	}
    stage('Compile') {
       steps {
          sh "mvn clean compile"
       }
    }

    stage('Test'){
       steps {
        // echo "test...."
        sh "mvn test"

	   }
	}
	stage('Integration Test'){
       steps {
         //echo "Integration test..."
          sh "mvn failsafe:integration-test failsafe:verify"

	   }
	}

    stage ('Package'){
      steps {
         sh "mvn package -DskipTests"
      }
    }

    stage('Build Docker Image'){
       steps {
        //"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
           script {
              dockerImage = docker.build("sureshcm1/currency-exchange-devops:${env.BUILD_TAG}")
           }
	   }
    stage('Push Docker Image'){
       steps {
        script {
           docker.withRegistry('','dockerhub'){  // credential ID
               dockerImage.push();
               dockerImage.push('latest');
           }

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
  


