node {
    def imageName = "vnewapp"
    def registryCredentials = "admin"
    def registry = "172.21.249.92:8123/"
    // def registry = "http://localhost:8081/repository/newdockerrepoprivate/"
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
        
        // sh "docker tag ${imageName}:latest 172.21.249.92:8123/"
       
        sh "docker login -u admin -p admin123 172.21.249.92:8123"
        // sh "docker push 172.21.249.92:8123/mydockerprivaterepo/${imageTag} ${nexusImageName}"

        docker.withRegistry('http://' + registry, registryCredentials) {
            dockerImage.push('latest')
        }
        
    }

    
}
    
   
