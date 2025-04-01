node{
    def app
    stage('Clone Repository') {
        checkout scm
         sh 'ls -l'  
    }
    stage('Build image') {
        sh 'docker --version'
        sh 'docker info'
        app = docker.build("kristijankrstevski/jenkins-pipeline-test")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
        }
    }
}