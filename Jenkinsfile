#!groovy
node {
    def PROJECT_NAME = "project_name"
	def scmVars = checkout scm
    // Clean workspace before doing anything
    // deleteDir()
	notifyFailed()
	mvn()

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
	
	bat 'cd NumberGenerator & mvn package'
	
}
