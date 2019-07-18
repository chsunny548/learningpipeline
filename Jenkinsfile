properties([parameters([string(defaultValue: 'Hello', description: 'How should I greet the world?', name: 'Greeting')])])

    stage('Checkout'){
        node {
	checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/chsunny548/simple-java-maven-app.git']]])
	}}
    stage('Build') {
	node('linux'){
        echo 'Building....'

	echo "Build id is $env.BUILD_ID \n Job name is $env.JOB_NAME"
	echo "$Greeting"
	withMaven() {
	   sh """
		mvn -B -DskipTests clean package
	"""
	}
	/*stash includes: '**/target/*.jar', name: 'app'*/
    }}
    stage('Test') {
	node {
        echo 'Testing....'
/*	unstash 'app'*/
    }}
    stage('Deploy') {
        node {
        echo 'Deploying....'
	if (currentBuild.result == null || currentBuild.result == 'SUCCESS') { 
            echo currentBuild.result
        }
    }}

