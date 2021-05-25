pipeline {
	
	  
	agent any
	
    stages {
        stage ('checkout scm') {
            steps {
                checkout(scm)
            }
        }

        stage ('Build') {
            steps {
            	container ('maven') {
                    sh 'mvn clean install -DskipTests=true'
                }
            }
        }
    }
    
}