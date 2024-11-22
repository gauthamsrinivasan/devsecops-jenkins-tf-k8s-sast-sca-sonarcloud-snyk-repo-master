pipeline {
  agent any
  tools { 
        maven 'Maven_3_2_5'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=gauthamsrinivasan_project -Dsonar.organization=gauthamsrinivasan -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=4f1b5bf8dde6e3e3a33f114083cf2a7919a65354'
			}
        }  

	stage('RunSCAAnalysisUsingSnyk') {
            steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}
    }		
  }
}
