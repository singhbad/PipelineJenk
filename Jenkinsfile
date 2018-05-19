#!groovy
pipeline
{
	agent any 
	environment 
	{
		def project_name = "Stage_Implementation"
		def branch_url_1 = "https://github.com/singhbad/PipelineJenk.git"
		def message 	 = "the build has started ${BUILD_NUMBER} ${BUILD_URL}"
	
	}
		
		stages
		{
			
			stage('emptyDirectory')
				{
					steps
					{
						deleteDir()
					}
				
				}
			
			
			stage('StartTheBuild')
				{
					steps
					{
						echo "message"
					}
				
				}
			
			stage('createDirectory')
				{
					steps
					{
						bat 'mkdir repo1'
						bat 'mkdir repo2'
					}
				
				}
			
			stage('checkoutMultiScm')
				{
					steps
					{
						
	
							checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'repo1']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/singhbad/PipelineJenk.git']]])
	
							checkout([$class: 'GitSCM', branches: [[name: '*/Jenkins_Dragon']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'RelativeTargetDirectory', relativeTargetDir: 'repo2']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/singhbad/Jenkins_Dragon.git']]])

						

					}
				
				}
				
			stage('mavenBuild')
				{
					steps
					{
						bat 'cd repo1/NumberGenerator & mvn package'
					}
				
				}
				
			


	}
	post {
        always {
            junit '**/target/*.xml'
        }
        /*failure {
            mail to: badal.singh@gmail.com, subject: 'The Pipeline failed :('
        }*/
    }


}