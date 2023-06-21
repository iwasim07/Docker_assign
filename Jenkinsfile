node {
    def imageName = "vnewapp"
    def registryCredentials = "admin"
    def registry = "http://172.21.249.92:8123/repository/"
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
    stage('Publish to Nexus') {
        steps {
            withDockerRegistry([credentialsId: registryCredentials, url: registry]) {
                // Tag the Docker image with the Nexus repository URL
                dockerImage = docker.image(imageName)
                dockerImage.tag("${registry}${imageName}")
                
                // Push the Docker image to the Nexus repository
                dockerImage.push()
            }
        }
    }

    // stage('Publish to Nexus') {
    //     def nexusUrl = 'http://' + registry
    //     def nexusRepo = 'mydockerprivaterepo' // Replace with your Nexus repository name
        
    //     def auth = '-u admin:admin123' // Replace with your Nexus credentials
        
    //     def imageTag = 'latest'
    //     def nexusImageName = "${nexusUrl}/${nexusRepo}/mydockerprivaterepo"
        
    //     sh "docker tag ${imageName}:${imageTag} ${nexusImageName}"
    //     sh "docker login -u admin -p admin123 172.21.249.92:8123"
    //     sh "docker push 172.21.249.92:8123/mydockerprivaterepo/${imageTag} ${nexusImageName}"
        
    // }

    
}
    
   
