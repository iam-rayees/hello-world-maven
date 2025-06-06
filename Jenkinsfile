pipeline {
  agent none

  stages {
    stage('Build & Run Java App') {
      agent {
        docker {
          image 'maven:3.8.1-adoptopenjdk-11'
          args '-v $HOME/.m2:/root/.m2'  // Cache Maven dependencies
        }
      }
      steps {
        sh 'mvn -B clean compile'
        sh 'mvn exec:java'
      }
    }

    stage('Front-end') {
      agent {
        docker { image 'node:16-alpine' }
      }
      steps {
        sh 'node --version'
      }
    }
  }
}
