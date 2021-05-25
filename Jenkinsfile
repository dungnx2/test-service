pipeline {
	
	  
	agent any
	
	tools { 
        maven 'maven'
        'org.jenkinsci.plugins.docker.commons.tools.DockerTool' '18.09'
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
        
        stage ('BuildDocker') {
            steps {
                    sh 'docker build -f Dockerfile -t dungnx2/test-service:1.0.1 .'
            }
        }
    }
    
}