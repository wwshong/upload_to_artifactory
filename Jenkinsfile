pipeline {
    agent any

    options {
        disableConcurrentBuilds()
    }

    stages {
        stage("create artifacts") {
            steps {
     
                 sh 'echo jenkins publishes artifacts to jfrog >> jenkins-jfog.txt '
            }
        }

        stage("upload artifacts") {
            steps {
			 echo "jenkins publishes artifacts to jfrog"
			  script {
			 def server = Artifactory.server "jenkins-jfrog-integ"
       def buildInfo = Artifactory.newBuildInfo()
       buildInfo.env.capture = true
       buildInfo.env.collect()
       def uploadSpec = """{
         "files": [
           {
             "pattern": "**/target/*.jar",
             "target": "/"
           }, {
             "pattern": "**/target/*.pom",
             "target": "/"
           }, {
             "pattern": "${WORKSPACE}/*.txt",
			"target": "{1}"
           }
         ]
       }"""
       // Upload to Artifactory.
       server.upload spec: uploadSpec, buildInfo: buildInfo
       buildInfo.retention maxBuilds: 10, maxDays: 7, deleteBuildArtifacts: true
       // Publish build info.
       server.publishBuildInfo buildInfo
	   }
		    }
		}
	}
}
