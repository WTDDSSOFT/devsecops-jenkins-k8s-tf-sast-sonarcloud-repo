pipeline {
  agent any
  tools { 
        maven 'Maven_3_8_4'  
    }
   stages {
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=wtdevsecops -Dsonar.organization=wtdevsecops -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=f2c44da401e175d20933d01fdd56171c95860a97'
			}
        }
	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }	
	   stage('Build') { 
			steps { 
			   withDockerRegistry([credentialsId: "dockerlogin", url: ""]) {
				 script{
				 app =  docker.build("asg")
				 }
			   }
			}
    }

	stage('Push') {
			steps {
				script{
					docker.withRegistry('https://609150809022.dkr.ecr.us-west-2.amazonaws.com', 'ecr:us-east-1:aws-credentials') {
					app.push("latest")
					}
				}
			}
	}
  }
}
