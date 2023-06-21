node {
    stage('Cloning code from GitHub'){
        git branch: 'master', url: 'https://github.com/iwasim07/Docker_assign.git'
    }

    // Building Docker images
    stage('Building Image') {
    	agent any
      steps {
      	sh 'docker build -t iwasim07/myapp:latest .'
      }
    }
}
    
   
