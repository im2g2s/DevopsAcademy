pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/im2g2s/DevopsAcademy.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
    }
}
