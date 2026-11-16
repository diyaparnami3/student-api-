pipeline {
    agent any

    tools {
        // Configure these names under Jenkins -> Manage Jenkins -> Tools
        maven 'Maven 3'
        jdk 'JDK 17'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo 'Resolving and downloading dependencies...'
                sh 'mvn dependency:resolve'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
            post {
                always {
                    // Archive JUnit test result reports
                    junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully.'
        }
        failure {
            echo 'Pipeline execution failed.'
        }
    }
}

