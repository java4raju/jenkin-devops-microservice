pipeline {

	//agent any
	agent {
        docker {
            image 'maven:3-alpine' 
            args '-v /root/.m2:/root/.m2' 
        }
    }

    environment{
    	dockerHome = tool 'myDocker'
    	mavenHome = tool 'myMaven'
    	PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
    }

	stages{

		stage('Compile') {
			steps{
			echo "Compile stage"
			sh "mvn clean compile"
			}
	}
	
	stage('Test') {
		steps{
		sh "mvn test"
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
