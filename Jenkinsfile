pipeline {
  agent any
  tools { 
        maven 'maven'  
    }
   stages{
    	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					bat 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
