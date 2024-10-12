node('ubuntu-Appserver-2140') {
    def app

    stage('Cloning Git') {
        /* Let's make sure we have the repository cloned to our workspace */
        checkout scm
    }

    stage('Build-and-Tag') {
        /* This builds the actual image */
        app = docker.build('omarelk18/car_docker_repo') 
    }
    
    stage('Post-to-DockerHub') {
        /* Ensure proper credentials for DockerHub are used */
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials') {
            /* Push the image to DockerHub */
            app.push('latest')
        }
    }

    stage('Deploy') {
        /* Deploy the new image using docker-compose */
        sh "docker-compose down"
        sh "docker-compose up -d"
    }
}
