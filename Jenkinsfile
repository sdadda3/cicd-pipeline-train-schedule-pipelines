pipeline {
  agent any
    stages {
      stage (build) {
        steps {
          echo 'Running build automation'
          echo "the current directory is:" sh 'pwd'
          sh './gradlew build --no-daemon'
          archiveArtifacts artifacts: 'dist/trainSchedule.zip'
       }
    }
  }
}

