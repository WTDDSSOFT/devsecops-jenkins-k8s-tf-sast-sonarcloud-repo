pipeline {
  agent any
  tools { 
        maven 'Maven_3_8_4'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=wtdevsecops -Dsonar.organization=wtdevsecops -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=f2c44da401e175d20933d01fdd56171c95860a97'
			}
        } 
  }
}
