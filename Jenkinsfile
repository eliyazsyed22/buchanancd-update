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
        stage('Static code Analysis'){
            
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
    }   
        
}