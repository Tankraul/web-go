pipeline {
    agent { label 'tuto' }
    environment {
        DOCKERHUB_CREDS = credentials('dockerhub-credentials')
    }
    stages {
        stage('Build') {
            steps {
                container('podman') {
                     script {
                        sh 'podman build -t docker.io/nelsonyaccuzzi/web-go:$BUILD_NUMBER -f Dockerfile'
                        sh 'podman login docker.io -u $DOCKERHUB_CREDS_USR -p $DOCKERHUB_CREDS_PSW'
                        sh 'podman push docker.io/nelsonyaccuzzi/web-go:$BUILD_NUMBER'
                    }
                }
                container('kubectl') {
                    script {
                        sh 'kubectl version'
                    }
                }
              container('fortune') {
                    script {
                        sh 'fortune'
                    }
              }
               
    }
        } stage('Deploy') {
            steps {
                container('kubectl') {
                    script {
                        sh 'kubectl apply -f manifest.yaml'
                    }
                }
            }
        }
    }
}

