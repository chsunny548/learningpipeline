pipeline {
	
	agent any
	environment {
	CRED = credentials('PASS')
	}
	stages{
		stage("Build"){
		steps{
		echo "Hello World"
		echo "$CRED"
		sh './hello.sh'
		}}
	

		stage("Test"){
		steps{
		echo "Testing"
		}}
	}
}
