node {
    def app
    stage('Clone Repository') {
        checkout scm
    }
    stage('Build Image') {
        app = docker.build("ankitadas478/testjenkinsnodesneha")
    }
    stage('Test Image') {
        app.inside {
            echo "Test Passed"
        }
    }
    stage('Push Image') {
        docker.withRegistry('https://registry.hub.docker.com ', 'docker-hub') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
        echo "Trying to push Docker Build to Dockerhub"
    }
}