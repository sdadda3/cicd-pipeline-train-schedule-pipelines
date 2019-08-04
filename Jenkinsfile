pipeline {
  agent any
    stages {
      stage (build) {
        steps {
          echo 'Running build automation'
          sh "echo The current directory is: view commen pwd below" 
          sh 'pwd'
          sh './gradlew build --no-daemon'
          archiveArtifacts artifacts: 'dist/trainSchedule.zip'
       }
    }
  }
}

