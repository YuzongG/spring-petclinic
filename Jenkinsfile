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
        sh './mvnw sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dlicense.skip=true'
      }
    }

    stage('Deployment') {
      steps {
        echo 'Starting to deploy...'
        sh '''./mvnw package
'''
        sh 'java -jar -Dserver.port=8083 target/*.jar'
      }
    }

  }
}