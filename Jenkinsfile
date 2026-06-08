pipeline {
    agent any

    environment {
        IMAGE_NAME = "abhikukreti/cicd-app"
        IMAGE_TAG  = "v1"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checkout ho gaya GitHub se'
                checkout scm
            }
        }

        stage('Test') {
            steps {
                echo 'Tests run ho rahe hain...'
                sh 'cd app && npm test'
            }
        }

        stage('Docker Build') {
            steps {
                echo 'Docker image build ho rahi hai...'
                sh "docker build -t ${IMAGE_NAME}:${IMAGE_TAG} -f docker/Dockerfile ."
            }
        }

        stage('Docker Push') {
            steps {
                echo 'Image Docker Hub pe push ho rahi hai...'
                withCredentials([usernamePassword(
                    credentialsId: 'dockerhub-creds',
                    usernameVariable: 'USER',
                    passwordVariable: 'PASS'
                )]) {
                    sh "echo $PASS | docker login -u $USER --password-stdin"
                    sh "docker push ${IMAGE_NAME}:${IMAGE_TAG}"
                }
            }
        }

    }

    post {
        success {
            echo 'Pipeline successfully complete!'
        }
        failure {
            echo 'Pipeline fail ho gayi — check karo!'
        }
    }
}
