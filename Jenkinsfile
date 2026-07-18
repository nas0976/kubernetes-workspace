pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Jenkins récupérera vos fichiers depuis votre repo GitHub
                checkout scm
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                // Application de vos manifestes sur le namespace wordpress-ns
                sh 'kubectl apply -f . -n wordpress-ns'
            }
        }
    }
}
