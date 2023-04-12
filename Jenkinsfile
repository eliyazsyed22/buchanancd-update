
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
                    withCredentials([string(credentialsId: 'githubpattoken', variable: 'gitcred')]) {
                        sh 'cat eks-deployment.yaml'
                        sh "sed -i 's+${APP_NAME}.*+${APP_NAME}:${BUILD_ID}+g' eks-deployment.yaml"
                        sh "cat eks-deployment.yaml"
                        sh "git config user.email eliyaz7134@gmail.com"
                        sh "git config user.name eliyazsyed"
                        sh "git add eks-deployment.yaml"
                        sh "git commit -m 'Done by Jenkins Job update manifest: ${BUILD_ID}'"
                        //sh "git remote add origin https://github.com/eliyazsyed22/buchanancd-update.git"
                        //sh "git push --force https://{eliyazsyed22}:{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}@github.com/eliyazsyed22/buchanancd-update.git HEAD:main"
                        //sh "git pull origin main"
                        sh "git push main origin git@github.com:eliyazsyed22/buchanancd-update.git"
                        //sh "git push https://github.com/eliyazsyed22/buchanancd-update.git main"
                    }
                           
                }
            }
        }
    }       
}