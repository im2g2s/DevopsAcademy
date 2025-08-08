pipeline {
    agent any
triggers {
        // Poll GitHub every 1 minute for changes
        pollSCM('* * * * *')
    }
stages {
        stage('Checkout') {
            steps {
                git branch: 'slave1', url: 'https://github.com/im2g2s/DevopsAcademy.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                // Example build command
                //sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Example test command

		}
	}
stage('Deploy') {
            steps {
                echo 'Deploying to $DEPLOY_PATH ...'
                // Sample deployment (replace with your actual command)
               // sh """
                //mkdir -p $DEPLOY_PATH
                //cp -r * $DEPLOY_PATH/
                echo 'Deployed at: ' $(date)
                //"""
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deployment successful.'
        }
failure {
            echo '❌ Build or Deployment failed.'
        }
    }
}
