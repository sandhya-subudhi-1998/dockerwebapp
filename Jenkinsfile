pipeline {
  environment {
    registry = "sandhyasubudhi1998/docker-test"
    registryCredential = 'docker-hub'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/sandhya-subudhi-1998/dockerwebapp.git'
      }
    }
   stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
   stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
   stage('Remove Unused docker image') {
      steps{
        echo "  "
      }
    }
  }
}
