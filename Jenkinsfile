properties([parameters([string(defaultValue: "Hello", description: "hello world", name: "Greeting")])])

stage('Checkout'){
	node {
	git 'https://github.com/chsunny548/simple-java-maven-app.git'
	}
}
stage('Build'){
	parallel linux: {
		node {
	echo "Hello World"
	echo env.BUILD_ID
	}
	},
	windows: {
		node {
		echo "This is windows"
		echo env.JOB_NAME
	}
	}
	docker.image('maven:3-alpine').inside('-v /var/jenkins_home/workspace/env.JOB_NAME:/app -w /app'){
	sh 'mvn -B -DskipTests clean package'
	}
}
