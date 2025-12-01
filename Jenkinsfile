pipeline {
    agent any

    environment {
        IMAGE_NAME = "python-print-app"
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/saldjadounia/TestApp'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    sh 'docker rm -f python-print-app || true'
                    sh 'docker run --name python-print-app python-print-app'
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline terminé avec succès !"
        }
        failure {
            echo "Pipeline échoué."
        }
    }
}

