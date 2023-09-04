pipeline {
    agent any

    stages {
         stage('Generate Output Log') {
            steps {
                script {
                    // Create and write to the output.log file
                    sh 'echo "This is the content of the output.log" > output.log'
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    echo "Building the code using Maven..."
                    // Use Maven to compile and package the code
                }
            }
            post {
                success{
                    script{
                        archiveArtifacts '**/output.log', allowEmptyArchive: true
                    }
                }
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo "Running unit tests using JUnit..."
                    // Use JUnit or another test automation tool for unit tests

                    echo "Running integration tests using Selenium..."
                    // Use a tool like Selenium or JUnit for integration tests
                }
            }
        }

        stage('Code Analysis') {
            steps {
                script {
                    echo "Running code analysis using SonarQube..."
                    // Integrate a code analysis tool (e.g., SonarQube) using Jenkins plugins
                     }
                }
            }

        stage('Security Scan') {
            steps {
                script {
                    echo "Performing security scan using OWASP ZAP..."
                    // Integrate a security scanning tool (e.g., OWASP ZAP) using Jenkins plugins
                }
            }
    post {
       
        failure {
            script{
                 mail from: "valour2417@gmail.com",
                     to: "valour2417@gmail.com",
                     subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                     body: "Pipeline failed. Check logs for details."
                     attachmentsPattern: '**/output.log' // Attach the output.log file on failure
            }
        }
       success { 
           script{
                mail from: "valour2417@gmail.com",
                     to: "valour2417@gmail.com",
                     subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                     body: "Pipeline succeeded. Logs attached."
                     attachmentsPattern: '**/output.log' // Attach the output.log file on success
           }
        }
    }

        }

        stage('Deploy to Staging') {
            steps {
                script {
                    echo "Deploying to staging server AWS EC2 instance..."
                    // Use a deployment script or tool to deploy to staging
                }
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo "Running integration tests on staging..."
                    // Use the same test automation tools as earlier to run integration tests on staging
                }
            }
   post {
        failure {
            script{
                 mail from: "valour2417@gmail.com",
                     to: "valour2417@gmail.com",
                     subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                     body: "Pipeline failed. Check logs for details."
                     attachmentsPattern: '**/output.log' // Attach the output.log file on failure
            }    
        }
        
        success { 
            script{
                 mail from: "valour2417@gmail.com",
                     to: "valour2417@gmail.com",
                     subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                     body: "Pipeline succeeded. Logs attached."
                     attachmentsPattern: '**/output.log' // Attach the output.log file on success
            }
        }
    }

        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploying to production server AWS EC2 instance..."
                    // Use a deployment script or tool to deploy to production
                }
            }
        }
    }
}
