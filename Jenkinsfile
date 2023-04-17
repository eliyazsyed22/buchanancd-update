
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
                        sh """
                       
                        git config --global user.name "eliyazsyed22"
                        git config --global user.email "eliyazsyed22@gmail.com"
                        whoami
                        echo $USER
                        //git fetch https://github.com/eliyazsyed22/buchanancd-update.git
                        //git rebase https://github.com/eliyazsyed22/buchanancd-update.git
                        git add eks-deployment.yaml
                        git commit -m 'Done by Jenkins Job update manifest: ${BUILD_ID}'
                        """
                    withCredentials([gitUsernamePassword(credentialsId: 'classictoken', gitToolName: 'Default')]) {
                                        
                                        sh "git push https://github.com/eliyazsyed22/buchanancd-update.git main"
                                    }

                }
            }
        }
    }       
}