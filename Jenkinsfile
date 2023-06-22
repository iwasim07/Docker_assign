node {
    def imageName = "vnewapp"
    def registryCredentials = "admin"
    def registry = "127.0.1.1:8123/"
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
        sh "docker login -u admin -p admin123 127.0.1.1:8123"
        sh "docker tag ${imageName}:latest 127.0.1.1:8123/${imageName}:latest"
        sh "docker push 127.0.1.1:8123/${imageName}:latest"
    }

    // Deploy to Kubernetes
    stage('Deploy to Kubernetes') {
        withKubeConfig([credentialsId: 'kubeconfig']) {
            // sh "docker login -u admin -p admin123 127.0.1.1:8123"
            sh 'eval $(minikube -p minikube docker-env)'
            sh 'kubectl apply -f secret.yaml'
            sh 'kubectl apply -f deployment.yaml'
        }
    }



}
    
   
