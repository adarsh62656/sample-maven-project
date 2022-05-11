pipeline {
  agent any
  stages {
    stage('build no'){
        when{
            branch "fix*"
        }
        steps {
        withCredentials([gitUsernamePassword(credentialsId: '13cf96f7-55a2-4dcf-82a7-18801da2b7a1', gitToolName: 'git-tool')]) {
        sh 'git fetch --all'
        }
        sh """
        git tag ${currentBuild.number}
        git push origin ${currentBuild.number}
        """
      }
    }
  }
}