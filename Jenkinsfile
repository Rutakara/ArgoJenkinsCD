pipeline {
  agent  any

  environment {

    DOCKERHUB_USERNAME = "dockerbenson"
    APP_NAME = "argocd-app"
    IMAGE_TAG = "${BUILD_NUMBER}"
    IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${APP_NAME}" + "${IMAGE_TAG}"
    REGISTRY_CRED = 'docker-cred'
  }
  
  stages {

      stage ('Clean Workspace') {

        steps {
           script {
             cleanWs()
           }
        }
      }
      stage ('Checkout') {

        steps {
          script {
            git credentialsId: 'github',
            url: 'https://github.com/Rutakara/ArgoJenkinsCD.git',
            branch: 'main'
          }

        }
      }
      stage ('Build') {
        steps {
          script {
            docker_image = docker.build "${IMAGE_NAME}"
          }
        }
      }
      

  }
  
}
