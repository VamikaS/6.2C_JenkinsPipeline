pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building the code using Maven tools..."
                    // Use Maven to compile and package the code
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
                // mail from: "valour2417@gmail.com",
                     emailext attachLog: true,   
                     subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                     body: "Pipeline failed. Check logs for details.",
                     to: "valour2417@gmail.com" 
            }
        }
       success { 
           script{
                //mail from: "valour2417@gmail.com",
                     emailext attachLog: true,
                     subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                     body: "Pipeline succeeded. Logs attached.",
                     to: '$DEFAULT_RECIPIENTS' //"valour2417@gmail.com" 
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
                // mail from: "valour2417@gmail.com",
                     emailext attachLog: true,
                     subject: "Pipeline Failed: ${currentBuild.fullDisplayName}",
                     body: "Pipeline failed. Check logs for details.",
                     to: '$DEFAULT_RECIPIENTS' 
            }    
        }
        
        success { 
            script{
                // mail from: "valour2417@gmail.com",
                     emailext attachLog: true,
                     subject: "Pipeline Successful: ${currentBuild.fullDisplayName}",
                     body: "Pipeline succeeded. Logs attached.",
                     to: '$DEFAULT_RECIPIENTS' //"valour2417@gmail.com"
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
