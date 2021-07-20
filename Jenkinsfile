pipeline {
  agent any
  triggers {
    pollSCM '* * * * *'
  }
  tools {
     maven 'M2_HOME'
  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
      } 
    }
     stage('Tomcat Deploy') {
      steps {
      deploy adapters: [tomcat8(credentialsId: 'TomcatID', path: '', url: 'http://10.0.0.39:8080/')], contextPath: null, war: '**/*war'
      } 
    }
  }
}
