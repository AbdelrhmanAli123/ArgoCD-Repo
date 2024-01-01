pipeline{
  agent any

  environment {
    GIT_REPO='https://github.com/AbdelrhmanAli123/GitOps-CD-k8s-Argocd-promethues-grafana'
    GIT_BRANCH='main'
    // IMAGE_NAME=''
  }
  stages{
    steps{
      
    stage(Code Checkout from Github){
      git credentialsId: 'github_cred', branch: "${GIT_BRANCH}" url: "${GIT_BRANCH}"
      }
    }
    stage(echo){
      steps{ 
        script{
          sh "echo ${IMAGE_VERSION}"
        }
      }
    }
  }
}
