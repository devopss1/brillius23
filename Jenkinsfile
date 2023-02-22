pipeline {
			agent any;

			tools {
				maven "MVN_HOME"
			}
		
			stages{
				stage('checkout'){
						steps{
							echo "Fetch the code from GitHub"
							git 'https://github.com/devopss1/brillius23.git'
						}
					}

				stage('Build'){
						steps{
							echo "mvn clean package"
							sh 'mvn clean package -f google/pom.xml'
						}
					}
				stage('Artifactory'){
						steps{
							echo "Uploading to nexus"
							nexusArtifactUploader artifacts: [[artifactId: 'google', classifier: '', file: '/root/.jenkins/workspace/job01/google/target/google.war', type: 'war']], credentialsId: 'Nexus', groupId: 'google.photos', nexusUrl: '192.168.0.12:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '2.0-SNAPSHOT'
							
						}
					}
				stage('Security Scan'){
						steps{
							echo "Scanning the security"
						}
					}
				stage('Deploy'){
						steps{
							echo "Deploy to production webserver"
						}
					}
	        }

	
}
