pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8s-id', namespace: 'app', serverUrl: 'https://376A67BA4DA2CF199C97BA2D58233193.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl create -f Deployment.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8s-id', namespace: 'app', serverUrl: 'https://376A67BA4DA2CF199C97BA2D58233193.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n app"
                }
            }
        }
    }
}
