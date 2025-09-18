pipeline {

    agent any
    stages {
	
        stage('CLONE SCM') {
            steps {
                echo 'This stage clones SC from GIT repo'				
				git branch: 'main', url: 'https://github.com/venkatdevops9678/mindcircuit16d_pom.xml.git'
            }
        }
		
        stage('Build Artifact') {
            steps {
                echo 'This stage builds the code using maven'
				sh 'mvn clean install'
				
            }
        }

		stage('Deploy Artifact') {
            steps {
                echo 'This stage DEPLOYS the code using maven'
				sh 'mvn clean deploy'
				
            }
        }

            stage('Deploy to Multiple Environments') {
            parallel {
                stage('Lab') {
                    steps {
                        echo 'DEPLOYING ON LAB...'
                       // deploying on LAB TOMCAT WEB SERVER 
                   }
                }
                stage('sbox') {
                    steps {
                        echo 'DEPLOYING ON sbox...'
                       // deploying on SBOX  TOMCAT WEB SERVER 
                   }
                    }
                
                stage('UAT') {
                    steps {
                        echo 'DEPLOYING ON UAT...'
                      // deploying on UAT  TOMCAT WEB SERVER 
                   }
                    }
                }
            }

			stage('Deploy to Tomcat') {
            steps {
                echo 'This stage deploys .war to tomcat webserver'
		deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://54.234.87.8:8080/')], contextPath: 'nexus_pipeline_deployment', war: '**/*.war'
        }
    }
	}
}
   

