peipeline 
{
agent 
{
	label "master"
	
}
tools {
		maven 'Maven3.1.1'
		jdk 'java8'
		}
		
		stages
		{
			stage('Intialize'){
			steps{
			bat '''
			echo "M2_HOME = %M2_HOME%"
			'''
					
			}
		}
		
		stage('Build'){
		steps
		{
		bat ' cd NumberGeberator & mvn package'
		}
		
		post {
		success {
		
		junit 'junit 'NumberGenerator/target/surefire-reports/*.xml'
		
		}
		
		}
		}

}
}