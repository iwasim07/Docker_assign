node {
    def imageName = "myphpapp"
    def registryCredentials = "nexus"
    def registry = "ec2-13-58-223-172.us-east-2.compute.amazonaws.com:8085/"
    def dockerImage = ''
    
    stage('Cloning code from GitHub'){
        git branch: 'master', url: 'https://github.com/iwasim07/Docker_assign.git'
    }

    stage('Building image') {
        dockerImage = docker.build(imageName)
    }
    // Building Docker images
    // stage("Build Docker Image") {
    //     checkout scm

    //     def dockerImageTag = "vnewapp:latest" // Replace with your desired image name and tag
    //     def dockerfilePath = "Dockerfile" // Replace with the path to your Dockerfile

    //     docker.build(dockerImageTag, "-f ${dockerfilePath} .")
    // }
}
    
   
