pipeline {
    agent any

    environment {
        // Define environment variables for AWS credentials
        AWS_ACCESS_KEY_ID = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
        AWS_DEFAULT_REGION = 'us-west-2'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from version control (e.g., Git)
                checkout scm
            }
        }

        stage('Terraform Init') {
            steps {
                // Initialize Terraform
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                // Show the Terraform execution plan
                sh 'terraform plan'
            }
        }

        stage('Terraform Apply') {
            steps {
                // Apply the Terraform configuration
                sh 'terraform apply -auto-approve'
            }
        }
    }

    post {
        success {
            echo 'Terraform apply was successful!'
        }

        failure {
            echo 'Terraform apply failed.'
        }
    }
}

