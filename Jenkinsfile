pipeline{
  agent any
  
  // parameters {
  //       string(name: 'IMAGE_VERSION', defaultValue: '', description: 'The version of the image')
  //   }
  environment {
    GIT_REPO='https://github.com/AbdelrhmanAli123/GitOps-CD-k8s-Argocd-promethues-grafana'
    GIT_BRANCH='main'
    IMAGE_NAME="${params.IMAGE_VERSION}"
  }
  stages{
    stage('Code Checkout from Github'){
     steps{
      git credentialsId:'github_cred', url: "${GIT_REPO}", branch: "main"
      }
    }
    stage('update the deployment file'){
      steps{ 
        script{
            sh "sed -i 's#image: abdelrhmandevops/devops-task-image#image: ${IMAGE_NAME}#' manifest_k8s_files/nodejs-deployment.yaml"
            sh "cat manifest_k8s_files/nodejs-deployment.yaml"
        }
      }
    }
    stage('push the updated deployment file to github repo'){
      steps{
        script{
          withCredentials([gitUsernamePassword(credentialsId: 'github_cred', gitToolName: 'Default')]) {
            sh """
            git config --globel user.name Abdelrhman
            git config --globel user.email balloabdelrhman@gmail.com
            git add .
            git commit -am "update the deployment file"
            git push https://github.com/AbdelrhmanAli123/GitOps-CD-k8s-Argocd-promethues-grafana main
            """
          }
        }
      }
    }
  }
}
