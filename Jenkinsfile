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
          dockerAngularImage = docker.build("angular-app", "-f angular-app/Dockerfile angular-app/")
        }
      }
    }
     stage('Building express') {
      steps{
        script {
          dockerExpressImage = docker.build("express-server", "-f express-server/Dockerfile express-server/")
        }
      }
    }
    stage('Deploy Angular') {
      steps{
        script {
           docker.withRegistry( registryfront , registryCredential ) {
           dockerAngularImage.push()
           }
        }
      }
    }
    
    stage('Deploy Express') {
      steps{
        script {
           docker.withRegistry( registryback , registryCredential ) {
             #je dois enlever les '' psk se sont des variables et je les ai déclaré en haut
           dockerExpressImage.push()
           }
        }
      }
    }
  }
}
