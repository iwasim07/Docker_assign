node {
    def imageName = "vnewapp"
    def registryCredentials = "nexus"
    def registry = "ec2-13-58-223-172.us-east-2.compute.amazonaws.com:8085/"
    def dockerImage
    
    // stage('Clone code from GitHub') {
    //     git branch: '*/master', credentialsId: 'githubwithpassword', url: 'https://bitbucket.org/ananthkannan/phprepo/'
    // }
    
    stage("Cloning code from GitHub") {
        steps {
            git(
                branch: 'master',
                credentialsId: 'githubwithpassword',
                url: 'https://github.com/iwasim07/Docker_assign/tree/master'
            )
        }
    }


    // Building Docker images
    // stage('Building Image') {
    // 	agent any
    //   steps {
    //   	sh 'docker build -t shanem/spring-petclinic:latest .'
    //   }
    // }

    // Uploading Docker images into Nexus Registry
    // stage('Push Docker Images to Nexus Registry'){
    //     sh 'docker login -u user -p password NexusDockerRegistryUrl'
    //     sh 'docker push NexusDockerRegistryUrl/Imagename}'
    //     sh 'docker rmi $(docker images --filter=reference="NexusDockerRegistryUrl/ImageName*" -q)'
    //     sh 'docker logout NexusDockerRegistryUrl'
    // }

    // Docker run
    // stage('Docker Run') {
    //     sh "docker run -d -p 85:80 --rm --name myapp ${registry}${imageName}"
    // }
}
