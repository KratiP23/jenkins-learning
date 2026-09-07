pipeline {

    agent {
        label 'linux-agent'
    }

    parameters {

        string(
            name: 'VERSION',
            defaultValue: '1.0.0',
            description: 'Application version'
        )

        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'staging', 'prod'],
            description: 'Select environment'
        )

        booleanParam(
            name: 'RUN_TESTS',
            defaultValue: true,
            description: 'Run automated tests'
        )
    }

    environment {
        APP_NAME = 'demo-app'
    }

    stages {

        stage('Build') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Version: ${params.VERSION}"
                echo "Environment: ${params.ENVIRONMENT}"

                sh '''
                    echo "Building application..."
                    echo "Build number: $BUILD_NUMBER"
                '''
            }
        }

        stage('Test') {

            when {
                expression {
                    params.RUN_TESTS
                }
            }

            steps {
                echo "Running tests..."

                sh '''
                    echo "Tests completed successfully"
                '''
            }
        }

        stage('Docker Check') {
        steps {
            sh '''
                echo "Checking Docker..."
                docker --version
                docker ps
            '''
            }
        }

        stage('Deploy to Dev') {

            when {
                expression {
                    params.ENVIRONMENT == 'dev'
                }
            }

            steps {
                echo "Deploying to DEV environment"
            }
        }

        stage('Deploy to Staging') {

            when {
                expression {
                    params.ENVIRONMENT == 'staging'
                }
            }

            steps {
                echo "Deploying to STAGING environment"
            }
        }

        stage('Deploy to Production') {

            when {
                expression {
                    params.ENVIRONMENT == 'prod'
                }
            }

            steps {
                echo "Deploying to PRODUCTION environment"
            }
        }
    }

    post {

        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }
    }
}