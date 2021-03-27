pipeline {
  agent any
  environment {
    registry = "amanibo/goMyCodeLabProject"
    registryCredential = 'dockerhub'
    HOME = '.'
  }
  
  stages {
    stage('Building angular') {
      steps{
        script {
          return docker.build("angular-app", "-f angular-app/Dockerfile ")
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
