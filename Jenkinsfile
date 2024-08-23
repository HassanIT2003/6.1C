pipeline {
    agent any

    // Define environment variables
    environment {
        TESTING_ENVIRONMENT = "stage"
        PRODUCTION_ENVIRONMENT = "Hassan Noonari"
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo "Using Maven for automated builds"
                    echo "Using a build automation tool to compile and package the code"
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Using JUnit for automated unit tests"
                    echo "Running unit tests"
                    echo "Using TestNG for integration tests"  // Replace [Tool Name] with the actual tool name for integration tests
                    echo "Running integration tests"
                }
            }
            post {
                success {
                    emailext(
                        subject: "Test Stage - Successful",
                        body: "All tests (unit and integration) passed successfully.",
                        to: "godofevergreen@gmail.com"
                    )
                }
                failure {
                    emailext(
                        subject: "Test Stage - Failed",
                        body: "One or more tests failed. Please check the logs for more details.",
                        to: "godofevergreen@gmail.com"
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo "Using SonarQube for code quality checks"
                    echo "Checking the quality of the code"
                }
            }
        }

        stage('Security Scan') {
            steps {
                script {
                    echo "Using AWS CodeDeploy for deployment"
                    echo "Deploying the application to the testing environment: ${env.TESTING_ENVIRONMENT}"
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Waiting for manual approval..."
                    sleep(time: 10, unit: 'SECONDS')  // Simulate manual approval with a 10-second delay
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                script {
                    echo "Using Kubernetes for production deployment"
                    echo "Deploying the code to the production environment: ${env.PRODUCTION_ENVIRONMENT}"
                }
            }
        }
    }
}



