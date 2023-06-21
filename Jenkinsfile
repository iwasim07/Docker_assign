node {
    def imageName = "vnewapp"
    def registryCredentials = "nexus101"
    def registry = "localhost:8081/repository/mydockerprivaterepo/"
    def dockerImage = ''

    def NEXUS_VERSION = "nexus3"
    def NEXUS_PROTOCOL = "http"
    def NEXUS_URL = "localhost:8081"
    def NEXUS_REPOSITORY = "vnewapp"
    def NEXUS_CREDENTIAL_ID = "NEXUS_CRED"

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

    stage("Publish to Nexus Repository Manager") {
            steps {
                script {
                    pom = readMavenPom file: "pom.xml";
                    filesByGlob = findFiles(glob: "target/*.${pom.packaging}");
                    echo "${filesByGlob[0].name} ${filesByGlob[0].path} ${filesByGlob[0].directory} ${filesByGlob[0].length} ${filesByGlob[0].lastModified}"
                    artifactPath = filesByGlob[0].path;
                    artifactExists = fileExists artifactPath;
                    if(artifactExists) {
                        echo "*** File: ${artifactPath}, group: ${pom.groupId}, packaging: ${pom.packaging}, version ${pom.version}";
                        nexusArtifactUploader(
                            nexusVersion: NEXUS_VERSION,
                            protocol: NEXUS_PROTOCOL,
                            nexusUrl: NEXUS_URL,
                            groupId: pom.groupId,
                            version: pom.version,
                            repository: NEXUS_REPOSITORY,
                            credentialsId: NEXUS_CREDENTIAL_ID,
                            artifacts: [
                                [artifactId: pom.artifactId,
                                classifier: '',
                                file: artifactPath,
                                type: pom.packaging],
                                [artifactId: pom.artifactId,
                                classifier: '',
                                file: "pom.xml",
                                type: "pom"]
                            ]
                        );
                    } else {
                        error "*** File: ${artifactPath}, could not be found";
                    }
                }
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
    
   
