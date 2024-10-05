pipeline {
    agent any
    
    environment {
        GIT_REPO = 'https://github.com/makkar207/6.1c.git'
        STAGING_SERVER = 'staging-server-address'
        PRODUCTION_SERVER = 'production-server-address'
        EMAIL_RECIPIENTS = 'infomakkar@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Stage 1: Build - Building the code using Maven'
                echo 'Tool: Maven'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Stage 2: Unit and Integration Tests - Running unit and integration tests using JUnit'
                echo 'Tool: JUnit'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Stage 3: Code Analysis - Analyzing the code using SonarQube'
                echo 'Tool: SonarQube'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Stage 4: Security Scan - Performing a security scan using OWASP Dependency-Check'
                echo 'Tool: OWASP Dependency-Check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Stage 5: Deploy to Staging - Deploying the application to the staging server'
                echo "Staging Server: ${env.STAGING_SERVER}"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Stage 6: Integration Tests on Staging - Running integration tests on the staging environment using Selenium'
                echo 'Tool: Selenium'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Stage 7: Deploy to Production - Deploying the application to the production server'
                echo "Production Server: ${env.PRODUCTION_SERVER}"
            }
        }
    }

    post {
        success {
            emailext to: "${env.EMAIL_RECIPIENTS}",
                     subject: "Jenkins Pipeline - Success: All stages completed",
                     body: "The Jenkins pipeline has completed successfully. Please find the attached log file.",
                     attachLog: true
        }

        failure {
            emailext to: "${env.EMAIL_RECIPIENTS}",
                     subject: "Jenkins Pipeline - Failure: Please check the logs",
                     body: "The Jenkins pipeline has failed. Please find the attached log file for more details.",
                     attachLog: true
        }

        always {
            echo "Pipeline execution completed."
        }
    }
}
