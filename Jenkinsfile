pipeline {
  agent any
  stages {
    stage('error') {
      parallel {
        stage('error') {
          steps {
            sh './mvnw clean package'
          }
        }

        stage('check convention') {
          steps {
            sh './mvnw pmd:check'
          }
        }

        stage('Sonar') {
          steps {
            sh '''./mvnw clean verify sonar:sonar \\
  -Dsonar.projectKey=Projet_SonarCube \\
  -Dsonar.host.url=http://sonarqube:9000 \\
  -Dsonar.login=ce7c48f319170b350652b34b031fce54666906fe'''
          }
        }

        stage('Nexus') {
          steps {
            sh './mvnw clean deploy -DskipTests'
          }
        }

      }
    }

  }
}