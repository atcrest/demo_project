pipeline{
	agent any
	tools{
		maven 'maven_home'
	}

	stages{
			stage ('Build'){

				steps{
					sh 'mvn clean package'

				}
				post {
					success{
						echo "Archiving the Artifacts"
						archieveArtifacts artifacts: '**/target/*.war'
					}
				}
			}

			stage ('Deply to Tomcat server') {
				steps{
					deploy adapters: [tomcat9(credentialsId: 'Tomcat_user', path: '', url: 'http://65.2.169.130:8090/')], contextPath: null, war: '**/*.war'
				}

			}

		} 

}