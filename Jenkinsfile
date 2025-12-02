pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/saldjadounia/TestApp.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-python-app .'
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker run --rm my-python-app'
            }
        }
    }
}



