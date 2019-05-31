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
        archiveArtifacts(artifacts: 'got/target/sandbox-1.0-SNAPSHOT.war', fingerprint: true)
      }
    }
    stage('Deploy') {
      steps {
        build(job: '../GOT-Deploy-to-Dev', parameters: [string(name: 'BRANCH_NAME', value: "${env.BRANCH_NAME}")])
      }
    }
  }
}