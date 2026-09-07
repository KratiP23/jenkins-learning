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
            steps {
                echo "RUN_TESTS = ${params.RUN_TESTS}"

                sh '''
                    echo "Running tests..."
                '''
            }
        }

        stage('Information') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Version: ${params.VERSION}"
                echo "Environment: ${params.ENVIRONMENT}"
                echo "Build: ${env.BUILD_NUMBER}"
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully"
        }

        failure {
            echo "Pipeline failed"
        }
    }
}