pipeline {
  agent node
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
        build job:'../GOT-Deploy-to-Dev' , parameters:[string(name: 'BRANCH_NAME', value: "${env.BRANCH_NAME}")]
      }
    }
  }
  
}
