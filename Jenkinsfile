pipeline {
    agent any     
    }   
    stages {
		stage('Check') {
            steps {
                echo 'Checking.'
                sh './quickstart/gradlew check -p quickstart/'
            }
        } 
        stage('Assemble') {
	          steps {
	              echo 'Building.'
		          sh 'chmod +x quickstart/gradlew'    
		          sh './quickstart/gradlew assemble -p quickstart'
	          }
      	}	    
        stage('Unit Test') {
	          parallel {
	              stage('test1') {
		                steps {
			                echo 'Execute Test1.'	
			                sh './quickstart/gradlew test -p quickstart'
		                }	
		             }
		             stage('test2') {
		                 steps {
			                 echo 'Execute Test2.'
			                 sh './quickstart/gradlew test -p quickstart'
		             }
		          }				
	          }
	    }	
	    stage('Deploy') {
	            steps {
	                echo 'Deploying.'
	            }
	        }
        } 		
	post {
        always {
            echo 'One way or another, I have finished'
        }    
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
	            mail to: 'melvi.caballero@gmail.com',
                     subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                     body: "Something is wrong with ${env.BUILD_URL}"
        }
        changed {
            echo 'Things were different before...'
        }
    }        
}    
