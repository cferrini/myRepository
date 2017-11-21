pipeline {
  agent any

  environment {
    MAJOR_VERSION = 1
  }
  
  options {
    buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '1'))
  }

  stages { 
    stage('test') {
      steps {
        sh 'ant -f test.xml -v'  
        junit 'reports/result.xml'
      }
    }
    stage('build') {
      steps {
        sh 'ant -f build.xml -v'
      }
    }
  }

  post {
    always {
      archive 'dist/*.jar'
    }
  } 
}
