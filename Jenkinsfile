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

		stage('Package Stage') {
		steps{
		echo "Packaging stage"
		sh "mvn package -DskipTests"
			}
		}

	stage('Docker build image stage') {
		steps{
		//docker build -t java4raju/currency-exchange-microservice:$env.BUILD_TAG
		script{
			dockerImage = docker.build("java4raju/currency-exchange-microservice:${env.BUILD_TAG}")
		}
			}
		}


	stage('Docker image push stage') {
		steps{
		script{
			dockerImage.push();
			dockerImage.push('latest');
		}
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
