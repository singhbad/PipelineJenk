#!groovy
pipeline
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
		bat ' cd NumberGenerator & mvn package'
		}
		
		stage('Display')
		{
		steps
		{
		echo 'Hello world!'
		
		}
		
		}
		
		post {
		success {
		
		junit 'NumberGenerator/target/surefire-reports/*.xml'
		
		}
		
		}
		

}
}
}
