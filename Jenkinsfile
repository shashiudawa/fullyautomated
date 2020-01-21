pipeline {
  environment {
    registry = "https://hub.docker.com/repository/docker/shashiudawa6022/test_tomcat"
    registryCredential = 'dockerregistry'
  }
  agent any
  stages {
    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('publish') {
      steps {
        script {
          docker.build registry + ":${env.BUILD_ID}"
        }
      }
    }
  }
}
