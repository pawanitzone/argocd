pipeline {
    agent any
    stages {
        stage ('Deploy_K8S') {
             steps {
                     withCredentials([string(credentialsId: "argocd-deploy-role", variable: 'ARGOCD_AUTH_TOKEN')]) {
                        sh '''
                        ARGOCD_SERVER="34.123.14.32"
                        APP_NAME="guestbook"
    
                        # Deploy to ArgoCD
                        ARGOCD_SERVER=$ARGOCD_SERVER argocd --grpc-web app sync $APP_NAME --force
                        ARGOCD_SERVER=$ARGOCD_SERVER argocd --grpc-web app wait $APP_NAME --timeout 600
                        '''
               }
            }
        }
    }

}
