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
	stage('Terraform plan'){
            steps{
		withCredentials([file(credentialsId: 'gcp_credentials', variable: 'gcp_creds')]) {
                	sh ('terraform plan')
            }
	}
        }
       stage('Terraform Apply'){
            steps {
                withEnv(['GCLOUD_PATH=/var/lib/jenkins/workspace/Jenkins_gcloud/google-cloud-sdk/bin']) {
                    withCredentials([file(credentialsId: 'gcp_credentials', variable: 'gcp_creds')]) {
                        sh '''
                        $GCLOUD_PATH/gcloud --version
                        $GCLOUD_PATH/gcloud auth activate-service-account --key-file ${gcp_creds}
			terraform apply  --auto-approve
                        '''
		    }
                    
                }
		    }
        }
    }
}
