pipeline {
  agent {
    node {
      label 'docker-vm'
    }

  }
  stages {
    stage('Check Out Code') {
      steps {
        git(url: 'https://github.com/avishai201/dotnet-core-api.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Build Image of Docker') {
      steps {
        sh 'docker build -t avishai201/todoapi:${BUILD_ID} .'
      }
    }
  
    stage('Push to DockerHub') {
      steps {
         withDockerRegistry(credentialsId: 'DockerHub-Creds') {
         sh 'docker push avishai201/todoapi:${BUILD_ID}'
       }
    }   
 }

    
}
}
