node {
    stage('Build') {
        echo 'Building....'
	sh './hello.sh'
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
