pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'qa'], description: 'Choose the environment')
    }

    environment {
        // You can use this to set global env vars based on the parameter
        TARGET_ENV = "${params.ENVIRONMENT}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/your-username/your-repo.git', branch: 'main'
            }
        }

        stage('Setup') {
            steps {
                echo "Setting up for environment: ${TARGET_ENV}"
                script {
                    if (TARGET_ENV == 'dev') {
                        echo 'Running DEV setup...'
                        // Add dev-specific setup commands here
                        sh 'echo "Dev environment setup complete"'
                    } else if (TARGET_ENV == 'qa') {
                        echo 'Running QA setup...'
                        // Add QA-specific setup commands here
                        sh 'echo "QA environment setup complete"'
                    }
                }
            }
        }

        stage('Build & Test') {
            steps {
                echo "Running build and tests for ${TARGET_ENV}"
                // Example: run tests with environment-specific config
                //sh "pytest --env=${TARGET_ENV}"
                sh 'Build & Test"'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully for ${TARGET_ENV}"
        }
        failure {
            echo "Pipeline failed for ${TARGET_ENV}"
        }
    }
}
