pipeline {

    agent any
    stages {
	
        stage('CLONE SCM') {
            steps {
                echo 'This stage clones SC from GIT repo'				
				git branch: 'main', url: 'https://github.com/devopstraininghub/mindcircuit16d.git'
            }
        }
		
        stage('Build Artifact') {
            steps {
                echo 'This stage builds the code using maven'
				sh 'mvn clean install'
				
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

        }
    }
   

