pipeline {
  agent any

  environment {
    IMAGE_NAME = 'stevetosak/jenkins-blueocean-homework'
  }

  stages {
    stage('Clone repo') {
      when {
        branch 'main'
      }
      steps {
        checkout scm
      }
    }

    stage('Build image') {
      when {
        branch 'main'
      }
      steps {
        script {
          app = docker.build("${IMAGE_NAME}")
        }
      }
    }

    stage('Push image') {
      when {
        branch 'main'
      }
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
          }
        }
      }
    }
  }
}

