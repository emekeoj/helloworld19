pipeline {
  agent any
  tools {
     maven 'M2_HOME'
  }
  environment {
    imagename = 'emekeoj/docker_jenkinsfile'
    registryCredential = 'DockerID'
    dockerImage = ''
  }
  stages {
    stage('Build Maven Job') {
      steps {
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
        sh 'mvn test'
      } 
    }
     stage('Build Docker Image') {
       steps {
         script {
           dockerImage = docker.build imagename
         }
       }
     }
     stage('Deploy Docker Image') {
       steps {
         script {
           docker.withRegistry( '', registryCredential) {
             dockerImage.push("$BUILD_NUMBER")
              dockerImage.push('latest')
           }
         }
       }
     stage('Tomcat Deploy') {
      steps {
      deploy adapters: [tomcat8(credentialsId: 'TomcatID', path: '', url: 'http://10.0.0.39:8080/')], contextPath: null, war: '**/*war'
      } 
     }
    }
  }
}
