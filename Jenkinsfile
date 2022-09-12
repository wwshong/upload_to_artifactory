pipeline {
    agent any

    options {
        disableConcurrentBuilds()
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
