pipeline{
    agent any
    stages{
        stage('Push Manifest'){
            steps{
                script{ 
                    withCredentials([usernamePassword(credentialsId: 'Github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config --local user.name '${GIT_USERNAME}'"
                        sh "git config --local user.email '${GIT_USERNAME}@gmail.com'"
                        sh "sed -i 's+naveed0004/spring.*+naveed0004/spring:${IMAGE_TAG}+g' dev/deployment.yaml"
                        sh "cat dev/deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job update artifact:v${IMAGE_TAG}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/SpringPipelineArtifact.git HEAD:master"
                    }
                }
            }
        }
    }
}
