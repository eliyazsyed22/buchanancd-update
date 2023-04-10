
pipeline{

    agent any

    stages {
        
        stage('Git Checkout'){
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                steps{
                
                    script{
                    
                        git branch: 'main', url: 'https://github.com/eliyazsyed22/buchananCIandCD.git'
                    }
                }
            }
            }
    }       
}
