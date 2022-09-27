pipeline{

	agent {label 'docker'}

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-rigistry')
	}

	stages {
	    
	    stage('gitclone') {

			steps {
				git 'https://github.com/meghagowda97/nodeapp_test.git'
			}
		}

		stage('Build') {

			steps {
				sh 'docker build -t meghadocker97/nodeapp_test:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push meghadocker97/nodeapp_test:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
