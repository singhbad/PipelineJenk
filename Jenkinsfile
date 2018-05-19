#!groovy
node 
{

	deleteDir()
    def PROJECT_NAME = "project_name"
	//def scmVars = checkout scm
	makeDirectory()
	multiRepoScmCheckOut()
	notifyFailed()
	mvn()

}

stages 
{ 	
	stage
	{
	def makeDirectory() 
		{
		bat 'mkdir repo1'
		bat 'mkdir repo2'
		}
	}
	stage
	{
	def notifyDeployedVersion(String version) 
		{
	emailext (
      subject: "Deployed: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: "DEPLOYED VERSION '${version}': Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]': Check console output at '${env.BUILD_URL}' [${env.BUILD_NUMBER}]",
      to: "badal.singh243@gmail.com"
			 )
		}
	}
	
	stage
	{
	def notifyFailed() 
		{
    emailext (
      subject: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
      body: "FAILED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]': Check console output at '${env.BUILD_URL}' [${env.BUILD_NUMBER}]",
      to: "badal.singh243@gmail.com"
			 )
		}
	}
	
	
	stage
	{
	def mvn() 
		{
			bat 'cd repo1/NumberGenerator & mvn package'
		}
	}

	
	stage
	{
	def multiRepoScmCheckOut() 
		{
	
		checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'repo1']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/singhbad/PipelineJenk.git']]])
	
		checkout([$class: 'GitSCM', branches: [[name: '*/Jenkins_Dragon']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'repo2']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/singhbad/Jenkins_Dragon.git']]])
		}
	}
}