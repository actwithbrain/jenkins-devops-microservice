pipeline {
	agent any
	//agent { docker { image 'maven:3.6.3' } }
	
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Checkout') {
			steps {
				echo "Checkout"
				sh 'mvn --version'
				sh 'docker version'
			}
		}

		stage('Compile') {
			steps {
				echo "Compile"
				sh 'mvn clean compile'
			}	
		}

		stage('Test') {
			steps {
				echo "Test"
				sh 'mvn test'
			}
		}
		
		stage('Integration Test') {
			steps {
				echo "Integration Test"
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
	}
}