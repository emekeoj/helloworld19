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
        sleep 10
      } 
    }
     stage('Deploy') {
      steps {
        echo "deploy step"
        sleep 10
      } 
    }
     stage('Docker') {
      steps {
        echo "image step"
        sleep 10
      } 
    }
  }
}
