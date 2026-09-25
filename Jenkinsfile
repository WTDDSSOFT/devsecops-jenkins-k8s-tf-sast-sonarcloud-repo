pipeline {
  agent any
  tools { 
        maven 'Maven_3_8_4'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=devsecopswtsantos -Dsonar.organization=devsecopswtsantos -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=1b588c4ac12cd297ef05cdc6b42be1d6373f299a'
			}
        } 
  }
}
