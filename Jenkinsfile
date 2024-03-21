pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/Yuzan-khadka/node-js-docker-app.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t yuzank/c0886439_assignment4:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push yuzank/c0886439_assignment4:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}