pipeline{
    agent any

    stages{
        stage('Checkout SCM'){
            steps{
                checkout([$class: ‘GitSCM’,
                branches: [[name: ‘*/feature]],
                extensions: [],
                userRemoteConfigs: [[url: ‘https://github.com/nabaansari9/learn-terraform-provision-gke-cluster.git‘]]])
            }
        }
    }
}
