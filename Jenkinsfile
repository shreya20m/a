pipeline{
	agent any
	environment{
		LANG='en_US.UTF-8'
		LC_ALL='en_US.UTF-8'
	}
	tools{
		maven 'Maven'
		}
	stages{
		stage('checkout'){
			steps{
				git branch:'master', url:'https://github.com/shreya20m/a.git'
			}
			}
		stage('build'){
			steps{
				sh 'mvn clean package'
			}
			}
		stage('Archive'){
			steps{
				archiveArtifacts artifacts: 'target/*war' , fingerprints=true  
			}
			}
		stage('Deploy'){
			steps{
				sh 'mvn clean package'
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
		}
	}
	}
	
}
