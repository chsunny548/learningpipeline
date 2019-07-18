properties([parameters([string(defaultValue: 'Hello', description: 'How should I greet the world?', name: 'Greeting')])])
node {
    stage('Checkout'){
	checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/chsunny548/simple-java-maven-app.git']]])
	}
    stage('Build') {
        echo 'Building....'

	echo "Build id is $env.BUILD_ID \n Job name is $env.JOB_NAME"
	echo "$Greeting"
	withMaven() {
   sh """
mvn -B -DskipTests clean package
"""
}
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
