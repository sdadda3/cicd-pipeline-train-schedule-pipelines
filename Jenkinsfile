pipeline {
  agent any
    stages {
      stage (build) {
        steps {
          echo 'Running build automation'
          pwd
          sh './gradlew build --no-daemon'
          archiveArtifacts artifacts: 'dist/trainSchedule.zip'
       }
    }
  }
}

