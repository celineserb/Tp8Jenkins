pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'C:\\Users\\esdi-pc\\Desktop\\SIL\\OUTILS\\Gradle\\gradle-5.6\\bin\\gradle build'
        bat 'C:\\Users\\esdi-pc\\Desktop\\SIL\\OUTILS\\Gradle\\gradle-5.6\\bin\\gradle javadoc'
        archiveArtifacts 'build/libs/*.jar'
        bat 'C:\\Users\\esdi-pc\\Desktop\\SIL\\OUTILS\\Gradle\\gradle-5.6\\bin\\gradle test'
        junit 'build/reports/tests'
      }
    }

  }
}