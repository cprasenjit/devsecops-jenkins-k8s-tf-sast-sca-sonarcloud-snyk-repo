pipeline {
  agent any
  tools { 
        maven 'maven'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		bat 'mvn clean verify sonar:sonar -Dsonar.projectKey=a-buggy-webapp -Dsonar.organization=buggy-webapp -Dsonar.host.url=https://sonarcloud.io/ -Dsonar.login=65169cb11f9d60499e53a245b54c59af20394eb5'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					bat 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
