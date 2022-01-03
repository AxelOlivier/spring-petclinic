pipeline {
  agent any
  stages {
    stage('error') {
      parallel {
        stage('error') {
          steps {
            sh './mvnw package'
          }
        }

        stage('check convention') {
          steps {
            sh './mvnw pmd:check'
          }
        }

      }
    }

  }
}