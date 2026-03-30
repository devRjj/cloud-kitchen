pipeline {
    agent any

    environment {
        IMAGE_NAME = "q2-app"
        CONTAINER_NAME = "c2"
        PORT = "90"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/devRjj/jenkins-demo2.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f $CONTAINER_NAME || true'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker run -d -p $PORT:80 --name $CONTAINER_NAME $IMAGE_NAME'
            }
        }
    }
}
