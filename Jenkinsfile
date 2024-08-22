pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                bat 'mvn clean install'  // Replace 'sh' with 'bat' for Windows
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                bat 'mvn test'  // Replace 'sh' with 'bat' for Windows
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing Code...'
                bat 'sonar-scanner'  // Replace 'sh' with 'bat' for Windows
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Performing Security Scan...'
                bat 'dependency-check.bat'  // Example: Replace 'sh' with 'bat' for Windows
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
                // Example: Use Windows-compatible deployment command
                bat 'scp target\\*.jar user@staging-server:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
                // Example: Use Windows-compatible command
                bat 'ssh user@staging-server "cd /path/to/app && ./run-tests.sh"'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
                // Example: Use Windows-compatible deployment command
                bat 'scp target\\*.jar user@production-server:/path/to/deploy'
            }
        }
    }
    post {
        always {
            echo 'Pipeline finished'
        }
        success {
            emailext (
                subject: "SUCCESS: Jenkins Pipeline",
                body: "The Jenkins pipeline completed successfully.",
                to: 'godofevergreen@gmail.com',
                attachLog: true
            )
        }
        failure {
            emailext (
                subject: "FAILURE: Jenkins Pipeline",
                body: "The Jenkins pipeline failed. Please check the logs.",
                to: 'godofevergreen@gmail.com',
                attachLog: true
            )
        }
    }
}

