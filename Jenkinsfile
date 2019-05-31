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
    stage('Stop Tomcat') {
      steps {
        dir(path: '${TOMCAT_DEV_HOME}\\bin') {
          sh './catalina.sh stop'
        }

      }
    }
    stage('Deploy') {
      steps {
        sh 'cp target\\*.war ${TOMCAT_DEV_HOME}\\webapps\\got.war'
      }
    }
    stage('Start Tomcat') {
      steps {
        dir(path: '${TOMCAT_DEV_HOME}\\bin') {
          sh 'catalina run'
        }

      }
    }
  }
  environment {
    TOMCAT_DEV_HOME = 'C:\\dev\\tools\\tomcat\\apache-tomcat-7.0.84'
  }
}