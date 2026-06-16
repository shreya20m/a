pipline{
	agent any
	tools{
		maven 'Maven'
		}
	stages{
		stage('checkout'){
			steps{
				git branch:'master', url:''
			}
			}
		stage('build'){
			steps{
				sh'mvn clean package'
			}
			}
		stage('Archive'){
			steps{
				sh'archiveArtifacts artifacts: 'target/*war' , fingerprints=true' 
			}
			}
		stage('Deploy'){
			steps{
				sh'mvn clean package'
				sh 'ansible-playbook ansible/playbook.yml -i ansible/hosts.ini'
		}
	}
	}
	
}
