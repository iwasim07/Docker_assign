node {
    def imageName = "vnewapp"
    def registryCredentials = "nexus101"
    def registry = "localhost:8081/repository/mydockerprivaterepo/"
    def dockerImage = ''

    // Cloning the Repo
    stage('Cloning code from GitHub'){
        git branch: 'master', url: 'https://github.com/iwasim07/Docker_assign.git'
    }

    //Building docker image
    stage('Building image') {
        dockerImage = docker.build(imageName)
    }

    // Uploading Docker images into Nexus Registry
    stage('Uploading to Nexus') {
        docker.withRegistry('http://' + registry, registryCredentials) {
            dockerImage.push('latest')
        }
    }
    
    // Building Docker images
    // stage("Build Docker Image") {
    //     checkout scm

    //     def dockerImageTag = "vnewapp:latest" // Replace with your desired image name and tag
    //     def dockerfilePath = "Dockerfile" // Replace with the path to your Dockerfile

    //     docker.build(dockerImageTag, "-f ${dockerfilePath} .")
    // }
}
    
   
