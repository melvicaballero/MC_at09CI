pipeline {
    agent any           
    stages {        
        stage('Assemble') {
            steps {
                echo 'compiling.'  
                sh 'chmod +x sampleWebApp/gradlew'              
                sh './sampleWebApp/gradlew assemble -p sampleWebApp'
                archiveArtifacts 'sampleWebApp/build/libs/**/*.jar'             
            }
        }       
        stage('Test') {
            steps {
                echo 'Executing Unit Test.'
                sh 'chmod +x sampleWebApp/gradlew'    
                sh './sampleWebApp/gradlew test -p sampleWebApp'                
            }
            post {
                always {
                    junit "sampleWebApp/build/test-results/test/*.xml"
                    archiveArtifacts 'sampleWebApp/build/reports/tests/test/*'
                }
            }
      	} 
        stage('sonarqube') {
            steps {
                echo 'sonarqube.'  
                sh 'chmod +x sampleWebApp/gradlew'              
                sh './sampleWebApp/gradlew sonarqube -p sampleWebApp'                             
            }
        }               
	stage('Deploy') {
	    steps {
	        echo 'Deploying.'
	    }	        
        }      		
    }       
}    
