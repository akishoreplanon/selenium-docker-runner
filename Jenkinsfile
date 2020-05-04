pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull kittu1023/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				sh "UID=${UID} GID=${GID} docker-compose up docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				sh "UID=${UID} GID=${GID} docker-compose up docker-compose up search-module book-flight-module"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
			sh "rm -rf output/"
		}
	}
}
