pipeline{
  agent any

  environment {
    GIT_REPO='https://github.com/AbdelrhmanAli123/GitOps-CD-k8s-Argocd-promethues-grafana'
    GIT_BRANCH='main'
    // IMAGE_NAME=''
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
          sh "echo ${IMAGE_VERSION}"
        }
      }
    }
  }
}
