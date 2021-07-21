pipeline {
  agent any
  stages {
    stage('build') {
      steps{
        mvn "clean"
        mvn "package"
        mvn "install"
      }
    }
  }
}

