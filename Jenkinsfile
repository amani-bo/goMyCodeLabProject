pipeline {
  agent any
  environment {
    registry = "amanibo/gomycodelabproject"
    registryCredential = 'dockerhub'
    dockerAngularImage = ''
    dockerExpressImage = ''
    HOME = '.'
    
  }
  
  stages {
    stage('Building angular') {
      steps{
        script {
          dockerAngularImage = docker.build("angular-app", "-f angular-app/Dockerfile angular-app/")
        }
      }
    }
     stage('Building express') {
      steps{
        script {
          return docker.build("express-server", "-f express-server/Dockerfile express-server/")
        }
      }
    }
    stage('Deploy Angular') {
      steps{
        script {
           docker.withRegistry( 'https://registry.hub.docker.com', dockerhub ) {
           dockerAngularImage.push()
           }
        }
      }
    }
    
    stage('Deploy Express') {
      steps{
        script {
           docker.withRegistry( 'https://registry.hub.docker.com', dockerhub ) {
           dockerExpressImage.push()
           }
        }
      }
    }
  }
}
