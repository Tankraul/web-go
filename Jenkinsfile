pipeline {
    agent { label 'tuto' }
    

    stages {
        stage('Build') {
            steps {
                container('podman') {
                    script {
                        sh 'podman build -t docker.io/tankraul/web-go -f Dockerfile'
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
    }
}
}
