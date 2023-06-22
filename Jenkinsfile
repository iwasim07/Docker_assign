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
        sh "docker login -u admin -p admin123 172.21.249.92:8123"
        sh "docker tag ${imageName}:latest 172.21.249.92:8123/${imageName}:latest"
        sh "docker push 172.21.249.92:8123/${imageName}:latest"
    }

    // Docker run
    // stage('Docker Run') {
    //     sh "docker run -d -p 87:80 --rm --name myappcontainer ${registry}${imageName}"
    // }

    // Deploy to Kubernetes
    stage('Deploy to Kubernetes') {
        withKubeConfig([credentialsId: 'kubeconfig']) {
            sh 'kubectl apply -f deployment.yaml'
        }
    }



}
    
   
