node
{
	
	
	stage{'Initialize'}
	{
	bat'''
		echo "M2_HOME=%M2_HOME%"
		'''
	
	}
	
	stage('Build')
	{
	bat 'cd NumberGenerator & mvn package'
	}
	
	stage('Test case')
	{
	 junit 'NumberGenerator/target/surefire-reports/*.xml, allowEmptyResults:true'
	}
	
	
	}