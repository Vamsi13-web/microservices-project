pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-vamsi', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://C7D4BE75D9929F405A243FB89CB8E264.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-vamsi', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://C7D4BE75D9929F405A243FB89CB8E264.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
