pipeline {
    agent any
 
    environment {
        IMAGE_NAME = "valentine-app"
        CONTAINER_NAME = "valentine-container"
    }
 
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/rammohan97/Spc.git'
            }
        }
 
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }
 
        stage('Stop Old Container') {
            steps {
                sh '''
                  docker stop $CONTAINER_NAME || true
                  docker rm $CONTAINER_NAME || true
                '''
            }
        }
 
        stage('Run New Container') {
            steps {
                sh '''
                  docker run -d \
                  --name $CONTAINER_NAME \
                  -p 80:80 \
                  $IMAGE_NAME
                '''
            }
        }
    }
}
 
