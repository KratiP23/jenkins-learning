pipeline {

    agent {
        label 'linux-agent'
    }

    environment {
        APP_NAME = 'demo-app'
        ENVIRONMENT = 'dev'
    }

    stages {

        stage('Build') {
            steps {
                echo "Application: ${env.APP_NAME}"
                echo "Environment: ${env.ENVIRONMENT}"

                sh '''
                    echo "Running build..."
                    echo "Build number: $BUILD_NUMBER"
                    echo "Workspace: $WORKSPACE"
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Testing ${env.APP_NAME}"

                sh '''
                    echo "Running tests..."
                    echo "Tests completed successfully"
                '''
            }
        }

        stage('Information') {
            steps {
                echo "Job: ${env.JOB_NAME}"
                echo "Node: ${env.NODE_NAME}"
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