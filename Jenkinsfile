pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: kubectl
    image: dtzar/helm-kubectl:latest
    command: ['cat']
    tty: true
'''
        }
    }
    stages {
        stage('Deploy to Kubernetes') {
            steps {
                container('kubectl') {
                    // La commande 'cat' laisse le conteneur ouvert 
                    // et permet au shell de Jenkins de s'exécuter normalement.
                    sh 'kubectl version --client'
                    sh 'kubectl apply -f . -n wordpress-ns'
                }
            }
        }
    }
}
