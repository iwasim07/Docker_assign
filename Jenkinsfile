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
        
        sh "docker tag ${imageName}:latest 172.21.249.92:8123/"
       
        sh "docker login -u admin -p admin123 172.21.249.92:8123"
        // sh "docker push 172.21.249.92:8123/mydockerprivaterepo/${imageTag} ${nexusImageName}"
        
    }

    
}
    
   
