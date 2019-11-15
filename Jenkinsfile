pipeline {
    agent any
    stages {
        stage('Build Image') {
            steps {
                bat "docker build -t yosua161/ppm-fe ."
            }
        }
        stage('Push Image') {
            steps {
			    withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'pass', usernameVariable: 'user')]) {
			        bat "docker login --username=${user} --password=${pass}"
			        bat "docker push yosua161/ppm-fe:latest"
			    }                           
            }
        }
    }
}