pipeline { 
    agent any  
 
    stages { 
        stage('Build') { 
            steps { 
                echo "Building the code"
                echo "Using a build automation tool like Maven"
            } 
        } 
        stage('Unit and Integration Tests') { 
            steps { 
                echo "Running unit tests"
                echo "Using test automation tools for unit and integration tests"
            } 
            post { 
                success { 
                    emailext subject: "Unit and Integration Tests Succeeded", 
                             body: "The Unit and Integration Tests stage completed successfully.", 
                             attachLog: true, 
                             to: "godofevergreen@gmail.com" 
                } 
                failure { 
                    emailext subject: "Unit and Integration Tests Failed", 
                             body: "The Unit and Integration Tests stage failed. See attached logs for details.", 
                             attachLog: true, 
                             to: "godofevergreen@gmail.com" 
                } 
            } 
        } 
        stage('Code Analysis') { 
            steps { 
                echo "Running code analysis"
                echo "Integrating a code analysis tool"
            } 
        } 
        stage('Security Scan') { 
            steps { 
                echo "Performing security scan"
                echo "Using a security scanning tool"
            } 
            post { 
                success { 
                    emailext subject: "Security Scan Succeeded", 
                             body: "The Security Scan stage completed successfully.", 
                             attachLog: true, 
                             to: "godofevergreen@gmail.com" 
                } 
                failure { 
                    emailext subject: "Security Scan Failed", 
                             body: "The Security Scan stage failed. See attached logs for details.", 
                             attachLog: true, 
                             to: "godofevergreen@gmail.com" 
                } 
            } 
        } 
        stage('Deploy to Staging') { 
            steps { 
                echo "Deploying to staging server"
                echo "Using deployment scripts to transfer the application to the staging environment"
            } 
        } 
        stage('Integration Tests on Staging') { 
            steps { 
                echo "Running integration tests on staging"
                echo "Using end-to-end test suites to validate the application in the staging environment"
            } 
        } 
        stage('Deploy to Production') { 
            steps { 
                echo "Deploying to production server"
                echo "Using deployment tools to push the final application to the production environment"
            } 
        } 
    } 
 
    post { 
        failure { 
            emailext subject: "Pipeline Failed", 
                     body: "Pipeline failed. See attached logs for details.", 
                     attachLog: true, 
                     to: "godofevergreen@gmail.com" 
        } 
        success { 
            emailext subject: "Pipeline Succeeded", 
                     body: "Pipeline succeeded. See attached logs for details.", 
                     attachLog: true, 
                     to: "godofevergreen@gmail.com" 
        } 
    } 
}


