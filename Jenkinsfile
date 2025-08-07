pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'qa'], description: 'Choose the environment')
    }

    environment {
        TARGET_ENV = "${params.ENVIRONMENT}"
    }

    stages {
        stage('Approval') {
            steps {
                script {
                    def userInput = input(
                        id: 'Approval', message: "Proceed with build for '${TARGET_ENV}' environment?",
                        parameters: [
                            booleanParam(defaultValue: true, description: 'Approve build execution', name: 'Approved')
                        ]
                    )
                    if (!userInput) {
                        error("Build not approved. Pipeline aborted.")
                    }
                }
            }
        }

        stage('Checkout') {
            steps {
                echo "📥 Checking out code from GitHub..."
                git url: 'https://github.com/im2g2s/DevopsAcademy.git', branch: 'test'
            }
        }

        stage('Setup') {
            steps {
                echo "⚙️ Setting up for environment: ${TARGET_ENV}"
                script {
                    if (TARGET_ENV == 'dev') {
                        bat "echo DEV environment setup complete"
                    } else if (TARGET_ENV == 'qa') {
                        bat "echo QA environment setup complete"
                    }
                }
            }
        }

        stage('Build') {
            steps {
                echo "🏗️ Building project for ${TARGET_ENV}"
                script {
                    if (TARGET_ENV == 'dev') {
                        bat "echo Building DEV artifacts"
                        // Add actual build commands here
                    } else if (TARGET_ENV == 'qa') {
                        bat "echo Building QA artifacts"
                        // Add actual build commands here
                    }
                }
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running tests for ${TARGET_ENV}"
                script {
                    if (TARGET_ENV == 'dev') {
                        bat "echo Running DEV tests"
                        // Example: bat "pytest --env=dev"
                    } else if (TARGET_ENV == 'qa') {
                        bat "echo Running QA tests"
                        // Example: bat "pytest --env=qa"
                    }
                }
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Deploying to ${TARGET_ENV} environment"
                script {
                    if (TARGET_ENV == 'dev') {
                        bat "echo Deploying to DEV"
                        // Add deployment logic here
                    } else if (TARGET_ENV == 'qa') {
                        bat "echo Deploying to QA"
                        // Add deployment logic here
                    }
                }
            }
        }

        stage('Report') {
            steps {
                echo "📊 Generating reports for ${TARGET_ENV}"
                bat "echo Report generation complete"
                // Integrate Allure or TestRail here if needed
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
