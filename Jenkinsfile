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
    stage('echo'){
      steps{ 
        script{
            sh "sed -i 's#image: abdelrhmandevops/devops-task-image#image: ${IMAGE_NAME}#' manifest_k8s_files/nodejs-deployment.yaml"
            sh "cat manifest_k8s_files/nodejs-deployment.yaml"
        }
      }
    }
  }
}
