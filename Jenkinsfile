pipeline {
  agent any
  environment {
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
           docker.withRegistry( 'amanibo/angularproject', dockerhub ) {
           dockerAngularImage.push()
           }
        }
      }
    }
    
    stage('Deploy Express') {
      steps{
        script {
           docker.withRegistry( 'amanibo/expressproject', dockerhub ) {
           dockerExpressImage.push()
           }
        }
      }
    }
  }
}
