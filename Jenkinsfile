pipeline {
    agent any

    environment {
        IMAGE_NAME = "q3-app"
        CONTAINER_NAME = "c3"
        PORT = "8081"
    }

    stages {

        stage('Clone Code') {
            steps {
                git 'https://github.com/devRjj/cloud-kitchen.git'
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
