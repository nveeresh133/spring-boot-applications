pipeline {
	agent any

	tools {
         maven 'maven'
         jdk 'openjdk-11'
    }

	stages {

		stage('Build'){
			steps {
// 				sh '''mvn install -s settings.xml'''
				sh '''mvn install -s settings.xml'''
			}
		}

		stage('Test'){
			steps{
				sh '''mvn test'''
			}
		}
		
		stage('Sonarqube') {
		     environment {
			 scannerHome = tool 'SonarQubeScanner'
			 }
			 steps {
				withSonarQubeEnv('sonarqube') {
		    // 		sh "sonar-scanner -Dsonar.projectKey=esp -Dsonar.projectName='esp'"
				sh "mvn clean verify sonar:sonar -Dsonar.projectKey=esp -Dsonar.projectName='esp'"
			 }

	           }
             }
}
}
