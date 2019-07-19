properties([parameters([string(defaultValue: "Hello", description: "hello world", name: "Greeting")])])

stage('Checkout'){
	node {
	git 'https://github.com/chsunny548/learningpipeline.git'
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
}
