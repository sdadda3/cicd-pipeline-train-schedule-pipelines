pipeline {
  agent any
    stages {
     stage (build) {
        steps {
          echo "${env.BRANCH_NAME}"
          echo 'Running build automation'
          sh './gradlew build --no-daemon'
          archiveArtifacts artifacts: 'dist/trainSchedule.zip'          
       }
    }
     stage('DeployToStaging') {
       when {
        branch 'master' 
       }
       steps {
        withCredentials([usernamePassword(credentialsId: 'webserver_login', usernameVariable: 'USERNAMO', passwordVariable: 'USERPWD')]) {
         sshPublisher(
           failOnError: true,         
           continueOnError: false,
           publishers: [
             sshPublisherDesc(
               configName: 'staging_serv',
               sshCredentials: [
                 username: "$USERNAMO",
                 encryptedPassphrase: "$USERPWD"
                 ];
               transfers: [
                 sshTransfer(
                   sourceFiles: 'dist/trainSchedule.zip',
                   removePrefix: 'dist/',
                   remoteDirectory: '/tmp',
                   execCommand: 'sudo /usr/bin/systemctl stop train-schedule && rm -rf /opt/train-schedule/* && unzip /tmp/trainSchedule.zip -d /opt/train-schedule && sudo /usr/bin/systemctl start train-schedule'
                   )
                 ]
               )
             ]
           )
        }
       }
     }
 }
}
