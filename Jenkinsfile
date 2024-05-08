pipeline {
    agent any

    stages {
        stage('Deploy to Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://20C7C4FADB03BABDEF32CEB5B908D246.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }
            }
        }
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://20C7C4FADB03BABDEF32CEB5B908D246.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
