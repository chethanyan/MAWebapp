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
		stage('Archieve'){
			steps{
				archieveArtifacts artifact:'target/*.war', fingerprint:true
			}
		}
		stage('build'){
			steps{
				sh 'mvn clean package'
				sh 'ansible-playbook playbook.yml -i hosts.ini'
			}
		}
	}
}
