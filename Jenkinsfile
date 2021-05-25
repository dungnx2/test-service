pipeline {
	
	  
	agent any
	
	tools { 
        maven 'Maven 3.8.1' 
    }
	
    stages {
        stage ('checkout scm') {
            steps {
                checkout(scm)
            }
        }

        stage ('Build') {
            steps {
                    sh 'mvn clean install -DskipTests=true'
            }
        }
    }
    
}