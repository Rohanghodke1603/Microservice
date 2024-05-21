pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://75B10BF66BD796AD04C53F9980FEDDA9.gr7.ap-south-1.eks.amazonaws.com') {
                  sh "kubectl apply -f deployment-service.yml"
                  
               }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://75B10BF66BD796AD04C53F9980FEDDA9.gr7.ap-south-1.eks.amazonaws.com') {
                  sh "kubectl get svc -n webapps"
               }
            }
        }
    }
}
