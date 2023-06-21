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
    // stage('Uploading to Nexus') {
    //     docker.withRegistry('http://' + registry, registryCredentials) {
    //         dockerImage.push('latest')
    //     }
    // }

    stage('Publish to Nexus') {
        def nexusUrl = 'http://' + registry
        def nexusRepo = 'your-nexus-repo' // Replace with your Nexus repository name
        
        def auth = '-u your-nexus-username:your-nexus-password' // Replace with your Nexus credentials
        
        def imageTag = 'latest'
        def nexusImageName = "${nexusUrl}/${nexusRepo}/${imageName}:${imageTag}"
        
        sh "docker tag ${imageName}:${imageTag} ${nexusImageName}"
        sh "docker login ${auth} ${nexusUrl}"
        sh "docker push ${nexusImageName}"
        sh "docker logout ${nexusUrl}"
    }
    
    // Building Docker images
    // stage("Build Docker Image") {
    //     checkout scm

    //     def dockerImageTag = "vnewapp:latest" // Replace with your desired image name and tag
    //     def dockerfilePath = "Dockerfile" // Replace with the path to your Dockerfile

    //     docker.build(dockerImageTag, "-f ${dockerfilePath} .")
    // }
}
    
   
