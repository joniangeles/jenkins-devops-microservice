pipeline {
	agent any
	// agent { 
	// 	docker { 
	// 		image 'maven:3.6.3' 
	// 	} 
	// }

	environment {
		dockerHome = tool 'docker'
		mavenHome = tool 'maven'
		PATH = "$PATH:$dockerHome/bin:$mavenHome/bin"
	}

	stages {
		stage('Checkout') {
			
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_URL - $env.BUILD_URL"
				
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps {
				sh "mvn test"
			}			
		}
		stage('Intagration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}			
		}
	} 
	post {
		always {
			echo 'This always runs'
		}
		success {
			echo 'Success'
		}
		failure {
			echo 'Fail'
		}
		changed {
			echo 'Build status changed.'
		}
	}
}
