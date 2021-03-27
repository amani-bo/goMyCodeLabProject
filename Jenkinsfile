pipeline {
  agent any
  environment {
    registryfront = "amanibo/angularproject"
    registryback = "amanibo/expressproject"
    registryCredential = 'dockerhub'
    dockerAngularImage = ''
    dockerExpressImage = ''
    
  }
  
  stages {
    stage('Building angular') {
      steps{
        script {
          dockerAngularImage = docker.build( registryfront , "-f angular-app/Dockerfile angular-app/")
        }
      }
    }
     stage('Building express') {
      steps{
        script {
          dockerExpressImage = docker.build( registryback , "-f express-server/Dockerfile express-server/")
        }
      }
    }
    stage('Deploy Angular') {
      steps{
        script {
           docker.withRegistry( '' , registryCredential ) {
           dockerAngularImage.push()
           }
        }
      }
    }
    
    stage('Deploy Express') {
      steps{
        script {
           docker.withRegistry( '' , registryCredential ) {
           dockerExpressImage.push()
           }
        }
      }
    }
  }
}
