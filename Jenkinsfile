pipeline {
  agent any
  stages {
    stage('Clone repo') {
      steps {
        checkout scm
      }
    }

    stage('Build image') {
      steps {
        script {
          app = docker.build("${IMAGE_NAME}")
        }
        
      }
        stage('Build image') {
            steps {
                script {
                    app = docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Push image') {
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
  environment {
    IMAGE_NAME = 'stevetosak/jenkins-blueocean-homework'
  }
}
