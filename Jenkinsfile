pipeline {
    agent { label 'tuto' }
    

    stages {
        stage('Build') {
            steps {
                container('podman') {
                    script {
                        sh 'podman run hello-world'
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
