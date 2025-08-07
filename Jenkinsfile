pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'qa'], description: 'Choose the environment')
    }

    environment {
        TARGET_ENV = "${params.ENVIRONMENT}"
    }

    stages {
        stage('Checkout') {
            steps {
                echo "Checking out code from GitHub..."
                git url: 'https://github.com/im2g2s/DevopsAcademy.git', branch: 'test'
            }
        }

        stage('Setup') {
            steps {
                echo "Setting up for environment: ${TARGET_ENV}"
                script {
                    if (TARGET_ENV == 'dev') {
                        echo 'Running DEV setup...'
                        bat "echo Dev environment setup complete"
                    } else if (TARGET_ENV == 'qa') {
                        echo 'Running QA setup...'
                        bat "echo QA environment setup complete"
                    }
                }
            }
        }

        stage('Build & Test') {
            steps {
                echo "Running build and tests for ${TARGET_ENV}"
                script {
                    if (TARGET_ENV == 'dev') {
                        bat "echo Running DEV build and tests"
                        // Add actual build/test commands here
                    } else if (TARGET_ENV == 'qa') {
                        bat "echo Running QA build and tests"
                        // Add actual build/test commands here
                    }
                }
            }
        }
    }

    post {
        success {
            echo "✅ Pipeline completed successfully for ${TARGET_ENV}"
        }
        failure {
            echo "❌ Pipeline failed for ${TARGET_ENV}"
        }
    }
}
