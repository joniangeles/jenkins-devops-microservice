pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
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
