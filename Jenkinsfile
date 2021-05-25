pipeline {
	
	  
	agent {
        docker {
            image 'maven:3.8.1-adoptopenjdk-11' 
            args '-v /root/.m2:/root/.m2' 
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