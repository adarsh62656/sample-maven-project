pipeline {
  agent any
  stages {
    stage('build no'){
        when{
            branch "fix*"
        }
        steps {
        echo "Build number is ${currentBuild.number}"
      }
    }
  }
}