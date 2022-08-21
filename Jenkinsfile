pipeline{
    agent any

    stages{
        stage('Checkout SCM'){
            steps{
                git branch: 'feature', credentialsId: 'git_credential', url: 'https://github.com/nabaansari9/learn-terraform-provision-gke-cluster.git'
            }
        }

        stage('Gcloud init'){
            steps {
            withEnv(['GCLOUD_PATH=/var/jenkins_home/google-cloud-sdk/bin']) {
                sh '$GCLOUD_PATH/gcloud --version'
                }
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
       /* stage('Terraform Apply'){
            steps{
                sh ('terraform apply  --auto-approve --no color')
            }
        } */
    }
}
