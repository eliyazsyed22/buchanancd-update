
pipeline{

    agent any

    environment{
        APP_NAME = "public.ecr.aws/p5u5p5h0/buchananecr"
        IMAGE_TAG = "${BUILD_ID}"
    }

    stages {
        
        stage('Update manifest file'){

                steps{
                    script{
                            sh 'cat eks-deployment.yaml'
                            sh "sed -i 's+${APP_NAME}.*+${APP_NAME}:${BUILD_ID}+${DOCKERTAG}+g' eks-deployment.yaml"
                            sh "cat eks-deployment.yaml"
                            sh "git add ."
                            //sh "git commit "
                            sh "git checkout -b main && git pull origin main"
                            sh "git pull --no-commit && git commit -m "Merge""
                            sh "git push origin https://github.com/eliyazsyed22/buchanancd-update.git "
                        }
                    }
        }
    }       
}
