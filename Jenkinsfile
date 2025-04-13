node {
    def app

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("user2106/your-image-name")
    }

    stage('Push image') {
        if (env.BRANCH_NAME == 'dev') {
            docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
                app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
                app.push("${env.BRANCH_NAME}-latest")
            }
        } else {
            echo "Skipping Docker push on branch: ${env.BRANCH_NAME}"
        }
    }
}
