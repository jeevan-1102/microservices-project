pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://471F09AB9D6C07FA19F9530E87962C9D.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://471F09AB9D6C07FA19F9530E87962C9D.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
