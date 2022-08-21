pipeline{
    agent any

    stages{
        stage('Checkout SCM'){
            steps{
                git branch: 'feature', credentialsId: 'git_credential', url: 'https://github.com/nabaansari9/learn-terraform-provision-gke-cluster.git'
            }
        }
        stage('Terraform init'){
            steps{
                sh ('terraform init')
            }
        }
        stage('Terraform validate'){
            steps{
                sh ('terraform validate')
            }
        }
        stage('Terraform Apply'){
            steps{
                sh ('terraform apply  --auto-approve --no-color')
            }
        }
    }
}
