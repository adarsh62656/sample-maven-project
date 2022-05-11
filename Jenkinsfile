pipeline {
  agent any
  stages {
    stage('build no'){
        when{
            branch "fix*"
        }
        steps {
        sh """
        git tag ${currentBuild.number}
        """
      }
    }
  }
}