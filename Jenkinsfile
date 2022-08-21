pipeline{
    agent any

    stages{
        stage('Checkout SCM'){
            steps{
                git branch: 'feature', credentialsId: 'git_credential', url: 'https://github.com/nabaansari9/learn-terraform-provision-gke-cluster.git'
            }
        }
    }
}
