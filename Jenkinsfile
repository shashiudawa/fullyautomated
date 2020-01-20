pipeline {
  environment {
    registry = "https://hub.docker.com/repository/docker/shashiudawa6022/test_tomcat"
    rxegistryCreidential = 'dockerregistry'
  }
  agent any
  stages {
    stage('build') {
      steps {
        sh 'mvn clean package'
        sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
      }
    }
    stage('publish') {
      steps {
        withDockerRegistry([ credentialsId: "$dockerregistry", url: "$registry" ]) {
          sh 'docker push tomcatwebapp:${env.BUILD_ID}'
      }
    }
  }
}
