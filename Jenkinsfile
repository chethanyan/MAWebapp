pipeline{
	agent any
	tools{
	maven 'Maven'
	}
	stages{
		stage('Checkout'){
			steps{
				git branch:'master', url:'https://github.com/chethanyan/MAWebapp.git'
			}
		}
		stage('Build'){
			steps{
				sh 'mvn clean package'
			}
		}
		stage('Archive'){
			steps{
				archieveArtifacts artifact:'target/*.war', fingerprint:true
			}
		}
		stage('Deploy'){
			steps{
				sh 'mvn clean package'
				sh 'ansible-playbook playbook.yml -i hosts.ini'
			}
		}
	}
}
