pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('fahmifiqih-dockerhub')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t fahmifiqih/backend:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push fahmifiqih/backend:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
