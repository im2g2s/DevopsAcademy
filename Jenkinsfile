pipeline {
    agent any
    triggers {
        // Poll GitHub every 1 minute for changes
        pollSCM('* * * * *')
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/im2g2s/DevopsAcademy.git', branch: 'Dev'
            }
        }
        stage('Build') {
            steps {
                echo 'Building the project....'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
    }
}
