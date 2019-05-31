pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh 'mvn compile -Dmaven.test.skip=true'
      }
    }
    stage('Test') {
      steps {
        sh 'mvn test'
      }
    }
    stage('Package') {
      steps {
        sh 'mvn package -Dmaven.test.skip=true'
      }
    }
    stage('Deploy') {
      steps {
        build 'GOT-Deploy-to-Dev'
      }
    }
  }
  environment {
    TOMCAT_DEV_HOME = ' /c/dev/tools/tomcat/apache-tomcat-7.0.84'
  }
}