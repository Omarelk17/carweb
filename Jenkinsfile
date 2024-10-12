node('ubuntu-Appserver-2140')
{
    def app
    stage('Cloning Git')
    {
        */Let's make sure we have the repository cloned to our workspace */
        checkout scm
    }
    stage('Build-and-Tag')
    /*This builds the actual image;
    /*This is synonymous to docker build on the command line*/

    app.docker.build('omarelk18/car_docker_repo') 
}

stage ('Post-to-dockerfile')
{

    docker.withRegistery('https://registery.hub.docker.com', 'dockerhub_credentials')

    stage('Deploy')
    {

        sh "docker-compose down"
        sh "docker-compose up -d"
    }
}