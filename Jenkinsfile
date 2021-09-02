pipeline {
	//agent any
	agent { docker { image 'maven:3.6.3' } }
	stages {
		stage('Build') {
			steps {
				sh "mvn --version"
				echo "Build"
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
