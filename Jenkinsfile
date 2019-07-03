pipeline {
    agent any           
    stages {        
        stage('Assemble') {
            steps {
                echo 'compiling.'  
                sh 'chmod +x sampleWebApp/gradlew'                
                sh './sampleWebApp/gradlew assemble -p sampleWebApp'                           
            }
        }       
        stage('Test') {
	    steps {
	        echo 'testing.'
	        sh 'chmod +x sampleWebApp/gradlew'    
	        sh './sampleWebApp/gradlew test -p sampleWebApp'
	    }
      	}         
	stage('Deploy') {
	    steps {
	        echo 'Deploying.'
	    }	        
        }      		
    }       
}    
