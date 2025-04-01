node{
    def app
    stage('Clone Repository') {
        checkout scm
    }
    stage('Build image') {
        app = docker.build("KristijanKrstevski/jenkins-pipeline-test")
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com/','66fb1af9-08a9-4e74-88cd-b1019b9d5947') {
            app.push("${env.BUILD_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BUILD_NAME}-latest")
        }
    }
}