node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("matejtod/kiiijenkins")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'DockerDesktop') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}
