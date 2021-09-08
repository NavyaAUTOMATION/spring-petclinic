
pipeline{
	agent {label 'master'}
	tools{ maven 'M3'}
	stages{
		stage('Checkout'){
			steps{
				git branch: 'deploy', url: 'https://github.com/AnjuMeleth/spring-petclinic.git'
			}
		}
		stage(' Build') {
			steps {
				bat 'mvn clean compile'
			}
		}
		stage(' Test') {
			steps {
				bat 'mvn test'
			}
		}
                stage(' Package') {
			steps {
				bat 'mvn package'
                                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
			}
		}	
		//stage(' Reports') {
			//steps {
				//bat 'mvn verify' 
                                //publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site/jacoco', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: ''])
			//}
		//}				
	}
}
