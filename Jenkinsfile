pipeline {

    agent {
        label 'linux-agent'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Source code has been checked out'
                sh 'pwd'
                sh 'ls -la'
            }
        }

        stage('Build') {
            steps {
                echo 'Building application'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
            }
        }

    }
}