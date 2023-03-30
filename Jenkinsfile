pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                    git branch: 'main', url: 'https://github.com/eliyazsyed22/buchananCIandCD.git'
                }
            }
        }
        stage('UNIT testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Maven Build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        /*stage('Static code Analysis'){
            
            steps{
                script{
                   withSonarQubeEnv(credentialsId: 'Sonarqube-token') {
                        sh "mvn clean package sonar:sonar"
                    }
                }
            }
        }
        stage('Quality Gate'){
            
            steps{
                script{
                   waitForQualityGate abortPipeline: false, credentialsId: 'Sonarqube-token'
                }
            }
        }
        stage('Upload Artifact to Nexus Repo'){
            
            steps{
                script{
                   nexusArtifactUploader artifacts: 
                   [
                        [   artifactId: 'springboot', 
                            classifier: '', file: 'target/Uber.jar', 
                            type: 'jar'
                        ]
                    ], 
                    credentialsId: 'BT-nexus', 
                    groupId: 'com.example', 
                    nexusUrl: '13.232.37.213:8081', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'buchananrepo-release', 
                    version: '1.0.0'
                }
            }
        }*/
        stage('Docker Image Build'){
            
            steps{
                script{
                   sh 'docker image build -t buchanan:v1.$BUILD_ID .'
                }
            }
        }
                
    }       
}