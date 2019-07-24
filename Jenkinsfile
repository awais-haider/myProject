pipeline {
  agent { label 'master' }
  tools {
    maven 'localMaven'
  }
  stages {
    stage('checkout') {
      steps {
        git 'https://github.com/awais-haider/myProject.git'
      }
    }
    stage('Build') {
      steps {
        bat 'mvn clean compile'
      }
    }
    stage('Test') {
      steps {
        bat 'mvn test'
        junit '**/target/surefire-reports/TEST-*.xml'
      }
    }
    stage('Package') {
      steps {
        bat 'mvn package'
      }
    }
  }
}
