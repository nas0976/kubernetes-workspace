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
    command: ['/bin/sh', '-c']
    args: ['sleep infinity']
    tty: true
'''
        }
    }
    stages {
        stage('Deploy to Kubernetes') {
            steps {
                container('kubectl') {
                    sh 'kubectl apply -f . -n wordpress-ns'
                }
            }
        }
    }
}
