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
                withSonarQubeEnv(credentialsId: 'Sonarqube-token') {
                        sh "mvn clean package sonar:sonar"
                    }
            }
        }
    }   
        
}