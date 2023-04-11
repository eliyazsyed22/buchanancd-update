
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
                            sh "sed -i 's+${APP_NAME}.*+${APP_NAME}:${BUILD_ID}+g' eks-deployment.yaml"
                            sh "cat eks-deployment.yaml"
                            sh "git config user.email eliyaz7134@gmail.com"
                            sh "git config user.name eliyazsyed"
                            sh "git add eks-deployment.yaml"
                            sh "git commit -m 'Done by Jenkins Job update manifest: ${BUILD_ID}'"
                            //sh "git branch -M main"
                            //sh "git remote add origin https://github.com/eliyazsyed22/buchanancd-update.git"
                            sh "git push"
                            //sh "git pull origin main"
                            //sh "git config core.commentChar ";""
                            //sh "git push origin main:https://github.com/eliyazsyed22/buchanancd-update.git"
                        }
                    }
        }
    }       
}
