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
		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}			
		}
		stage('Build Docker Image') {
			steps {
				//"docker build -t joniangeles/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("joniangeles/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}			
		}
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('','dockerhub') {
						dockerImage.push();
						dockerImage.push("latest");
					}
					
				}
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
