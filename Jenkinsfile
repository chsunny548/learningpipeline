node {
    stage('Build') {
        echo 'Building....'
	sh './hello.sh'
    }
    stage('Test') {
        echo 'Testing....'
    }
    stage('Deploy') {
        echo 'Deploying....'
	if (currentBuild.result == 'SUCCESS') { 
            echo currentBuild.result
        }
    }
}
