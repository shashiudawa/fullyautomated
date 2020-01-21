pipeline {
  environment {
    registry = "https://index.docker.io/v1/"
    registryCredential = 'dockerregistry'
  }
  agent any
  stages {
    stage('build') {
      steps {
        sh 'mvn clean package'
        sh "docker build . -t shashiudawa6022/jenkins:${env.BUILD_ID}"
      }
    }
    stage('publish') {
      steps {
        withDockerRegistry([ credentialsId: "$registryCredential", url: "$registry" ]) {
          sh "docker push shashiudawa6022/jenkins:${env.BUILD_ID}"
        }
      }
    }
  }
}
