pipeline { 
    agent any 
    stages { 
        stage('Deploy To Kubernetes') { 
            steps { 
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'citatech-cluster', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://FEBA1C114C8C346E6D59F02CDBFAACF7.sk1.us-west-1.eks.amazonaws.com'
                ]]) { 
                    sh "kubectl apply -f deployment-service.yml" 
                } 
            } 
        } 
        stage('Verify Deployment') { 
            steps { 
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '', 
                    clusterName: 'citatech-cluster', 
                    contextName: '', 
                    credentialsId: 'k8-token', 
                    namespace: 'webapps', 
                    serverUrl: 'https://FEBA1C114C8C346E6D59F02CDBFAACF7.sk1.us-west-1.eks.amazonaws.com'
                ]]) { 
                    sh "kubectl get svc -n webapps" 
                } 
            } 
        } 
    } 
}
