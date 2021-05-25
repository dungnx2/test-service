pipeline {
	
	agent {
	    node {
	      label 'maven'
	    }
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