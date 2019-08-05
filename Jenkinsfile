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
    stage('Sonar') {
      steps {
       bat 'mvn sonar:sonar -Dsonar.projectKey=test -Dsonar.host.url=http://localhost:9000 -Dsonar.login=ab394b17e76cbbd7bd07e82e59221b30e18c0931' 
      }
    }
  }
}
