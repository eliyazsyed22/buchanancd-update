
pipeline{

    agent any

    stages {
        
        stage('Update manifest file'){

                steps{
                    script{
                            sh """
                            cat eks-deployment.yaml
                            sed -i 's/${public.ecr.aws/p5u5p5h0/buchananecr}.*/${v1.$BUILD_ID}/g' eks-deployment.yaml
                            cat eks-deployment.yaml 
                            """
                        }
                    }
        }
    }       
}
