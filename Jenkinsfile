pipeline {
    agent any

    stages {
        stage ('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Freensh/Node_app.git'
            }
        }

        stage ('Build and push backend and frontend images to ECR'){
            steps {
                sh '''
                cd ecr
                terraform init
                terraform apply -auto-approve
                '''
            }
        }
        
        stage ('Initialising the terraform code'){
            steps{
                
                sh 'terraform init'
            }
        }
        stage ('Deploying the app to ECS'){
            steps{
                sh 'terraform apply --auto-approve'
            }
        }
    }
}