pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/votre-compte/TestApp.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("python-print-app:latest")
                }
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker rm -f python-print-app || true'
                sh 'docker run --name python-print-app python-print-app:latest'
            }
        }
    }
    post {
        success {
            echo '✅ Pipeline réussi !'
        }
        failure {
            echo '❌ Pipeline échoué.'
        }
    }
}
