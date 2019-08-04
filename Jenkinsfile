pipeline {
  agent any
    stages {
      stage (build) {
        steps {
          sh 'printenv'
          echo "${env.BRANCH_NAME}"
          echo 'Running build automation'
          sh "echo The current directory is: view command pwd below" 
          sh 'pwd'
          sh './gradlew build --no-daemon'
          archiveArtifacts artifacts: 'dist/trainSchedule.zip'          
       }
    }
  }
}

