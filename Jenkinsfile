
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
                    withCredentials([gitUsernamePassword(credentialsId: 'newpat', gitToolName: 'Default')]) {
                        sh 'cat eks-deployment.yaml'
                        sh "sed -i 's+${APP_NAME}.*+${APP_NAME}:${BUILD_ID}+g' eks-deployment.yaml"
                        sh "cat eks-deployment.yaml"
                        sh "git config user.email eliyaz7134@gmail.com"
                        sh "git config user.name eliyazsyed"
                        sh "git add eks-deployment.yaml"
                        sh "git commit -m 'Done by Jenkins Job update manifest: ${BUILD_ID}'"
                        sh "git remote set-url origin github.com/eliyazsyed22/buchanancd-update.git"
                        sh "git remote -v"
                        sh "git branch -a"
                        sh "git checkout main"
                        sh "git branch -a"
                        //sh "git push --set-upstream origin main"
                        //sh "git remote add origin https://github.com/eliyazsyed22/buchanancd-update.git"
                        //sh "git push --force https://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@github.com/eliyazsyed22/buchanancd-update.git HEAD:main"
                        //sh "git pull origin main"
                        //sh "git push main origin https://github.com/eliyazsyed22/buchanancd-update.git"
                        sh "git push -u origin main"
                    }

                           
                }
            }
        }
    }       
}
