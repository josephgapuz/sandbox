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
        pwd()
        sh 'cp target/*.war ${TOMCAT_DEV_HOME}/webapps'
      }
    }
  }
  environment {
    TOMCAT_DEV_HOME = 'C:\\dev\\tools\\tomcat\\apache-tomcat-7.0.84'
  }
}