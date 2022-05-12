pipeline {
  agent any
  stages {
    stage('build no'){
        when{
            branch "fix*"
        }
        steps {
        withCredentials([gitUsernamePassword(credentialsId: '3622ccbe-3900-49f8-bf6c-8e003974bb3f', gitToolName: 'git-tool')]) {
        sh 'git fetch --all'
        sh """
        git tag build-${currentBuild.number}
        git push origin build-${currentBuild.number}
        """
        }
        
      }
    }
  }
}