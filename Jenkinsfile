#!groovy
node {

	deleteDir()
    def PROJECT_NAME = "project_name"
	//def scmVars = checkout scm
	
	makeDirectory()
	multiRepoScmCheckOut()
	
	
    // Clean workspace before doing anything
    
	notifyFailed()
	mvn()

}

def makeDirectory() {

	bat 'mkdir repo1'
	bat 'mkdir repo2'

}


def notifyDeployedVersion(String version) {
  emailext (
      subject: "Deployed: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: "DEPLOYED VERSION '${version}': Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]': Check console output at '${env.BUILD_URL}' [${env.BUILD_NUMBER}]",
      to: "badal.singh243@gmail.com"
    )
}

def notifyFailed() {
  emailext (
      subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]': Check console output at '${env.BUILD_URL}' [${env.BUILD_NUMBER}]",
      to: "badal.singh243@gmail.com"
    )
}

def mvn() {
	
	bat 'cd repo1/NumberGenerator & mvn package'
	
}

def multiRepoScmCheckOut() {
	dir('repo1') 
	{
		git url: 'https://github.com/singhbad/PipelineJenk.git'
		//branches: '[[name: '*/master]]' 
	}
	dir('repo2')
	{
		git url: 'https://github.com/singhbad/Jenkins_Dragon.git' 
		//branches: '[[name: '*/Jenkins_Dragon]]'
	}

}
