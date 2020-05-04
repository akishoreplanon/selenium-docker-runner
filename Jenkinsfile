pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh label: '', script: 'docker pull kittu1023/selenium-docker'
			}
		}
		stage("Start Grid"){
			steps{
				sh label: '', script: 'UID=${UID} GID=${GID} docker-compose up -d hub chrome firefox'
			}
		}
		stage("Run Test"){
			steps{
				sh label: '', script: 'UID=${UID} GID=${GID} docker-compose up docker-compose up search-module book-flight-module'
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh label: '', script: 'docker-compose down'
			sh label: '', script: 'rm -rf output/'
		}
	}
}
