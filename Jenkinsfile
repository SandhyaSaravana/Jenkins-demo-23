pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('Please')
	}

	stages {
        stage('git') {
            steps {
                git branch: 'main', credentialsId: 'pravin-git', url: 'https://github.com/pravin0306/pravinrepo.git'
            }
        }
		stage('Build') {

			steps {
				sh "docker build -t pravin0306/pravin-repo:04 /var/lib/jenkins/workspace/Py/python/"
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
                sh 'docker push pravin0306/pravin-repo:04'
			}
		}
	}}
