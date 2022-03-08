pipeline {

	agent any

	stages{

		stage('Build') {
			steps{
			echo "Build stage"
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
