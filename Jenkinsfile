pipeline {
  agent any
  triggers {
    pollSCM '* * * * *'
  }
  tools {
    maven 'M2_HOME'
  }
  stages {
    stage('build') {
      steps{
        sh 'mvn clean'
        sh 'mvn install'
        sh 'mvn package'
        sh 'mvn test'
      }
    }
    stage ('deloy to tomcat') {
      steps {
        deploy adapters: [tomcat8(credentialsId: 'TomcatID', path: '', url: 'http://10.0.0.39:8080/')], contextPath: null, war: '**/*.war'
      }
    }
  }
}

