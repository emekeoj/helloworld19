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
     stage('Test') {
      steps {
        echo "test step"
      
      } 
    }
     stage('Deploy') {
      steps {
        echo "deploy step"
      } 
    }
     stage('Docker') {
      steps {
        echo "image step"
      } 
    }
  }
}
