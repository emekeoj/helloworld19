pipeline {
  environment {
    imagename = "emekeoj/jenkinsfile"
    registryCredential = 'emekeoj-dockerhub'
    dockerImage = ''
  }
  agent any
  //triggers {
   // pollSCM '* * * * *'
  //}
  tools {
    maven 'M2_HOME'
  }
  stages {
    stage('build') {
      steps{
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'

      }
    }
    stage ('deloy to tomcat') {
      steps {
        deploy adapters: [tomcat8(credentialsId: 'TomcatID', path: '', url: 'http://10.0.0.39:8080/')], contextPath: null, war: '**/*.war'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build imagename
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push("$BUILD_NUMBER")
              dockerImage.push('latest')
          }
        }
      }
    }
  }
}

