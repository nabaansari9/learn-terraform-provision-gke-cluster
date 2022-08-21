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
                withCredentials([file(credentialsId: 'gcp_credentials', variable: 'gcp_creds')]) {
                    sh '''
                    gcloud auth activate-service account --key-file="$gcp_creds"
                    terraform apply  --auto-approve
                    '''
                }
                
            }
        }
    }
}
