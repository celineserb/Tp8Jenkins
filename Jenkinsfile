pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'C:\\Users\\esdi-pc\\Desktop\\SIL\\OUTILS\\Gradle\\gradle-5.6\\bin\\gradle build'
        bat 'C:\\Users\\esdi-pc\\Desktop\\SIL\\OUTILS\\Gradle\\gradle-5.6\\bin\\gradle javadoc'
        archiveArtifacts 'build/libs/*.jar'
        bat 'C:\\Users\\esdi-pc\\Desktop\\SIL\\OUTILS\\Gradle\\gradle-5.6\\bin\\gradle test'
        junit 'build/test-results/test/*'
      }
    }

    stage('MailNotification') {
      steps {
        mail(subject: 'succes', body: 'succes', bcc: 'hc_serbouh@esi.dz', cc: 'hc_serbouh@esi.dz')
      }
    }

    stage('cucember reports') {
      steps {
        cucumber 'Features/matrix.feature'
      }
    }

    stage('deploiment ') {
      steps {
        bat 'C:/Users/esdi-pc/Desktop/SIL/OUTILS/Gradle/gradle-5.6/bin/gradle publish'
      }
    }

    stage('Slack Notification') {
      steps {
        slackSend(attachments: 'Succes !', baseUrl: 'https://hooks.slack.com/services/', token: 'T01MYASFQ84/B01SKTK7LLD/JazTO4XphowwSzdniCa1Jj3R', blocks: 'Hello', channel: '#general', message: 'hello pipeline execute avec succes! ! ', username: 'celine', sendAsText: true, teamDomain: 'channel')
      }
    }

  }
}