pipeline {

	//agent any
	agent {
  docker {
    image 'maven:3-alpine'
    args '-v /var/jenkins_home/.m2:/root/.m2'
  }
}

	stages{

		stage('Build') {
			steps{
			echo "Build stage"
			sh "mvn --version"
			}
	}
	
	stage('Test') {
		steps{
		echo "Test stage"
		}
	}

	stage('Integration Test') {
		steps{
		echo "Integration Test stage"
			}
		}
	}

	post{
		always{
			echo "I run always"
		}

		success{
			echo "I run when success"
		}

		failure{
			echo "I run when failure"
		}
	}
	
}
