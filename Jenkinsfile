node {
    def imageName = "vnewapp"
    def registryCredentials = "nexus101"
    def registry = "172.21.249.92:8123/repository/"
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

    // stage('Publish to Nexus') {
    //     def nexusUrl = 'http://' + registry
    //     def nexusRepo = 'mydockerprivaterepo' // Replace with your Nexus repository name
        
    //     def auth = '-u admin:admin123' // Replace with your Nexus credentials
        
    //     def imageTag = 'latest'
    //     def nexusImageName = "${nexusUrl}/${nexusRepo}/${imageName}:${imageTag}"
        
    //     // sh "docker tag ${imageName}:${imageTag} ${nexusImageName}"
    //     sh "docker login -u admin -p admin123 172.21.249.92:8123"
    //     sh "docker push 172.21.249.92:8123/repository/mydockerprivaterepo/vnewapp:latest"
        
    // }
    // sh "docker tag ${imageName}:${imageTag} ${nexusUrl}/${nexusRepo}/${imageName}:${imageTag}"

    
}
    
   
