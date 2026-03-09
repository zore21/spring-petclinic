pipeline {
    agent any

    tools {
        maven 'Maven_3_9_13'
    }

    environment {
        IMAGE_NAME = "petclinic"
        TAG = "latest"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/zore21/spring-petclinic'
            }
        }
        stage('Build Jar') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:${TAG}")
                }
            }
        }

    }

}