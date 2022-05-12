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
        sh "docker build -t adarsh62656/gs-spring-boot-docker ."
        sh "aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/s5o7d0z2"
        sh "docker build -t adarsh-repo ."
        sh "docker tag adarsh-repo:build-${currentBuild.number} public.ecr.aws/s5o7d0z2/adarsh-repo:build-${currentBuild.number}"
        sh "docker push public.ecr.aws/s5o7d0z2/adarsh-repo:build-${currentBuild.number}"
      }
    }
  }
}