pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Compiling and packaging the code using Maven.'
                echo 'Tool: Maven - A build automation tool used for compiling and packaging Java code.'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running unit tests with JUnit and integration tests.'
                echo 'Tools: JUnit - A framework for writing and running unit tests in Java; Selenium - For integration testing.'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Analyzing the code quality using SonarQube.'
                echo 'Tool: SonarQube - A static code analysis tool that detects bugs, code smells, and security vulnerabilities.'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Performing a security scan using OWASP Dependency-Check.'
                echo 'Tool: OWASP Dependency-Check - Identifies vulnerabilities in project dependencies.'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying the application to a staging environment.'
                echo 'Tool: AWS CLI - Used to manage deployment to AWS EC2 instances.'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests in the staging environment.'
                echo 'Tool: Postman - Tool for testing APIs, used here for validating the deployed application in staging.'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying the application to the production environment.'
                echo 'Tool: AWS CLI - Used to deploy the application to a production server in AWS.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
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



