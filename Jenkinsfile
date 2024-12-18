pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials') // Add DockerHub credentials in Jenkins
        DOCKER_IMAGE = "cjas9/python-app"
    }

    stages {
        stage('Jasleen - Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t %DOCKER_IMAGE% .'
                }
            }
        }

        stage('Jasleen - Login to Dockerhub') {
            steps {
                script {
                    sh 'echo %DOCKERHUB_CREDENTIALS_PSW% | docker login -u %DOCKERHUB_CREDENTIALS_USR% --password-stdin'
                }
            }
        }

        stage('Jasleen - Push image to Dockerhub') {
            steps {
                script {
                    sh 'docker push %DOCKER_IMAGE%'
                }
            }
        }
    }
}
