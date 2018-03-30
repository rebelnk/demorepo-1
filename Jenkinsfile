pipeline {
	    agent any 
	       //tools {
	              //maven 'Maven-3.5.3'
	       //}
	
	  parameters {
        string(defaultValue: '', description: '', name: 'version')
		  
    }
	    stages {
	       
	           
	        stage('compile') { 
	            steps {
	                  
	                 
	                  withMaven(maven : 'Maven-3.5.3') {
	                         // echo "${params.version}"
				 // bat 'mvn compile -Dparams.version=%params.version%' 
				  bat 'mvn compile -Dparams.version=%params.version%'
				  
	                  }
	            }
	        }
	        stage('Test') { 
	            steps {
	               bat 'mvn test' 
	            }
	        }
	        stage('package') { 
	            steps {
	               bat 'mvn package -Dmaven.test.skip=true -Dparams.version=%params.version%'
	            }
	        }
		     stage('sonar') { 
	            steps {
	               bat 'mvn sonar:sonar -Dmaven.test.skip=true -Dparams.version=%params.version%'
	            }
	        }
		    
		    
		     stage('Deploy') { 
	            steps {
	               bat 'mvn deploy -Dmaven.test.skip=true -Dparams.version=%params.version%' 
	            }
	        }
		    
		    		    
		    
		   
		    
	    }
	}

