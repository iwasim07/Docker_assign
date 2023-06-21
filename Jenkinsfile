node {
    stage('Cloning code from GitHub'){
        git branch: 'master', url: 'https://github.com/iwasim07/Docker_assign.git'
    }

    // Building Docker images
    stage("Build Docker Image") {
        checkout scm

        def dockerImageTag = "vnewapp:latest" // Replace with your desired image name and tag
        def dockerfilePath = "Dockerfile" // Replace with the path to your Dockerfile

        docker.build(dockerImageTag, "-f ${dockerfilePath} .")
    }
}
    
   
