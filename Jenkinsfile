pipeline {
	
	  
	agent any

	
	environment {
        DOCKER_CREDENTIAL_ID = 'docker-id'
        REGISTRY = 'docker.io'
    }
	
    stages {
        stage ('checkout scm') {
            steps {
                checkout(scm)
            }
        }
        
        stage ('Sonar Scan') {
        	environment {

                scannerHome = tool 'sonar'

            }
            steps {
            	withSonarQubeEnv("sonar") {
                	sh '${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=sonar-test1 -Dsonar.sources=src/main/java -Dsonar.sourceEncoding=UTF-8 -Dsonar.language=java -Dsonar.java.binaries=.'
            	}
            }
        }

        stage ('Build') {
            steps {
                    sh 'mvn clean install -DskipTests=true'
            }
        }
        
        stage ('Build Docker File') {
            steps {
                    sh 'docker build -f Dockerfile -t dungnx2/test-service:1.0.1 .'
            }
        }
        
        stage ('Push to Docker Hub') {
            steps {
                    withCredentials([usernamePassword(passwordVariable : 'DOCKER_PASSWORD' ,usernameVariable : 'DOCKER_USERNAME' ,credentialsId : "$DOCKER_CREDENTIAL_ID" ,)]) {
                        sh 'echo "$DOCKER_PASSWORD" | docker login $REGISTRY -u "$DOCKER_USERNAME" --password-stdin'
                        sh 'docker push  dungnx2/test-service:1.0.1'
                    }
            }
        }
    }
    
}