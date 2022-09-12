pipeline {
    agent any

    options {
        disableConcurrentBuilds()
    }

	environment {
		
		FOO = "bar"
		
	}
    stages {
        stage("create artifacts") {
            steps {
               echo "jenkins publishes artifacts to jfrog" > jenkins-jfog.txt  
                 
            }
        }

        stage("upload") {
            steps {
			 echo "jenkins publishes artifacts to jfrog"
		    }
		}
	}
}
