pipeline{
	agent any
		stages{
				stage('SCM Checkout'){steps{
						git 'https://github.com/KirtiVyas/maven-project.git'}
							}
				stage('compile source code'){steps{
							withMaven (maven: 'LocalMaven'){
								sh 'mvn compile'}
							}
												}
			 	stage('test'){steps{
							withMaven (maven: 'LocalMaven'){
								sh 'mvn test'}
							}
								}
			stage('Sonar Analysis package'){steps{
			withSonarQubeEnv ('sonar'){
			withMaven (maven: 'LocalMaven'){
			sh 'mvn clean package sonar:sonar'}
			}
				      }
						       }
						     
		stage('install'){steps{
							withMaven (maven: 'LocalMaven'){
								sh 'mvn install'}
							}
								}
		}
}
			//stage('deploy to tomcat'){steps
			//{
			//sshagent(['45c07079-ce59-4923-8353-cc6f63d9622f']) {
			//sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.25.90:/var/lib/tomcat/webapps'
//}
			//}

						 //}
