pipeline {
  environment {
    registry = "amanibo/goMyCodeLabProject"
    registryCredential = 'dockerhub'
    HOME = '.'
  }
  agent any
  stages {
    stage('Building angular') {
      steps{
        script {
          return docker.build("angular-app", "-f angular-app/Dockerfile .")
        }
      }
    }
     stage('Building express') {
      steps{
        script {
          return docker.build("express-server", "-f express-server/Dockerfile .")
        }
      }
    }
  }
}
