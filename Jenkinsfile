pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: kubectl
    image: bitnami/kubectl:latest
    # On remplace le shell par une commande qui force l'exécution
    command: ['/bin/sh', '-c']
    args: ['while true; do sleep 30; done;']
    tty: true
'''
        }
    }
    stages {
        stage('Deploy to Kubernetes') {
            steps {
                container('kubectl') {
                    // Vérifions d'abord si la commande est bien reconnue
                    sh 'kubectl version --client'
                    sh 'kubectl apply -f . -n wordpress-ns'
                }
            }
        }
    }
}
