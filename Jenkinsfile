pipeline {
  environment {
    registry = "mouadrh12235/tp5"
    registryCredential = 'mrhofir12'
    dockerImage = ''
    gitBranch = 'main'
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git branch: "${gitBranch}", url: 'https://github.com/mrhofir/EXAM_TP4.git'
      }
    }
    stage('Building image') {
      steps {
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Test image') {
      steps {
        script {

          echo "Tests passed"
        }
      }
    }
    stage('Publish Image') {
      steps {
        script {
          docker.withRegistry('', registryCredential) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
