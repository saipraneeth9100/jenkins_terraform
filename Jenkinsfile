pipeline {
    agent any
    
    environment {
        PATH = "$PATH:/usr/local/bin"
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }
 stages {
        stage('Checkout') {
            steps {
                // Checkout your Terraform code from the Git repository
                git branch: 'main', url: 'https://github.com/saipraneeth9100/terraform-aws-ec2-instance.git'
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
                // Run Terraform plan to see what changes will be made
                sh 'terraform plan -out=tfplan'
            }
        }
        
        stage('Terraform Apply') {
            steps {
                // Apply the Terraform plan to create the EC2 instance
                sh 'terraform apply -auto-approve tfplan'
            }
        }
    }
}
