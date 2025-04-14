node {

	def app
	stage('Clone repo'){
		checkout scm
	}
	stage('Build image'){
		app = docker.build("stevetosak/jenkins-blueocean-homework")
	}
	stage('Push image'){
		docker.withRegistry('https://registry.hub.docker.com','dockerhub'){
			app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
			app.push("${env.BRANCH_NAME}-latest")
			
		}
	}
}
