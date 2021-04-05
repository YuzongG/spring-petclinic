pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './mvnw clean install -Dlicense.skip=True'
      }
    }

    stage('Test') {
      steps {
        sh './mvnw sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dlicense.skip=true -Dsonar.login="75fc2ea7d482e67eea394c58d10ff9cc4c98bfdf"'
      }
    }

    stage('Deployment') {
      steps {
        echo 'Starting to deploy...'
        sh '''./mvnw package
'''
        sh 'java -jar -Dserver.port=8083 target/*.jar &'
      }
    }

  }
}