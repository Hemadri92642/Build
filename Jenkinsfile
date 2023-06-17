#!groovy

pipeline {
	agent none
  stages {
  	stage('Maven build') {
    	agent {
      	docker {
        	image 'maven:3.5.0'
        }
      }
      steps {
      	sh 'mvn clean install'
      }
    }
    stage('Sonarqube build') {
    	 agent any
      steps {
      	sh ''' mvn clean verify sonar:sonar \
  -Dsonar.projectKey=Build \
  -Dsonar.projectName='Build' \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.token=sqp_dae5d410c3cddfe3bb0e4a873b3a0b981c4adaa0
'''
      }
    }
    
  }
}
