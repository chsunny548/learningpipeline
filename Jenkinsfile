properties([parameters([string(defaultValue: 'Hello', description: 'How should I greet the world?', name: 'Greeting')])])
node {
    
    stage('Build') {
        echo 'Building....'
	sh './hello.sh'
	echo "$CREDS"
	echo "Build id is $env.BUILD_ID \n Job name is $env.JOB_NAME"
    }
    stage('Test') {
        echo 'Testing....'
    }
    stage('Deploy') {
        echo 'Deploying....'
	if (currentBuild.result == null || currentBuild.result == 'SUCCESS') { 
            echo currentBuild.result
        }
    }
}
