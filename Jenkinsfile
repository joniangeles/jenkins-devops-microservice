pipeline {
	//agent any
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
		stage('Build') {
			
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_URL - $env.BUILD_URL"
				
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}			
		}
		stage('Intagration Test') {
			steps {
				echo "Integration Test"
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
