node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Push image') {
        when {
            branch 'dev'
        }
        steps {
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
                app.push("${env.BRANCH_NAME}-latest")
            }
        }
    }
}

