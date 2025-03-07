pipeline {
    agent any
    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
    }
    stages {
        stage('Terraform Init') {
            steps {
                bat 'terraform init'
            }
        }
        stage('Terraform Plan') {
            steps {
                bat 'terraform plan'
            }
        }
        stage('Terraform Apply') {
            steps {
                bat 'terraform apply -auto-approve'
            }
        }
        stage('Terraform Destroy') {
            when {
                expression {
                    return params.DESTROY == true
                }
            }
            steps {
                bat 'terraform destroy -auto-approve'
            }
        }
    }
}
