properties([parameters([string(defaultValue: 'Hello', description: 'How should I greet the world?', name: 'Greeting')])])

    stage('Checkout'){
        node {
	checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[url: 'https://github.com/chsunny548/simple-java-maven-app.git']]])
	}}
    stage('Build') {
     node {
     docker.image('maven:3-alpine').inside('-v /var/jenkins_home/workspace/learningpipeline:/app -w /app') {
        
            sh 'mvn --version'
	    sh 'mvn -B -DskipTests clean package'
        
    }
	archiveArtifacts '**/target/*.jar'
	stash includes: '**/target/*.jar', name: 'app'
}


}
    stage('Test') {
	
	parallel linux:{
	node{
        echo 'Building....'

	echo "Build id is $env.BUILD_ID \n Job name is $env.JOB_NAME"
	echo "$Greeting"
    }},
	 windows: {
	node{
	echo 'Hekki'
      }}

	
     docker.image('maven:3-alpine').inside('-v /var/jenkins_home/workspace/learningpipeline:/app -w /app') {
        
            sh 'mvn --version'
	    sh 'mvn test'
        
    }
	junit '**/target/**/*.xml'

}
    stage('Deploy') {
        node {
        echo 'Deploying....'
	if (currentBuild.result == null || currentBuild.result == 'SUCCESS') { 
            echo currentBuild.result
		sh 'java -jar ./target/*.jar'
        }
    }}

